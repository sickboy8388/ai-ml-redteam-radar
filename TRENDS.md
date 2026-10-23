# AI-ML-RedTeam Radar — Trend ledger

Single source of truth. The README and reports are derived from this file.
Last updated: 2026-10-23

Trend stages: `seed` → `emerging` → `accelerating` → `mainstreaming` → `dormant`.
Evidence line format: `date — primary URL — one line of context`. Max 10 per trend.

---

## trends

### id: local-inference-001 — Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)
- stage: emerging
- confidence: high
- last_evidence: 2026-10-12
- aliases: [Bleeding Llama, Breaking Local AI Runtimes]
- notes: Critical CVE cluster spanning the entire local/self-hosted inference stack (llama.cpp, Ollama, vLLM, LMDeploy, NVIDIA Triton, Xinference, SGLang); attack classes include GGUF parser overflows, server use-after-free, SSRF via multimodal endpoints, authentication bypass, and pickle deserialization bypass. In-the-wild exploitation confirmed (LMDeploy CVE-2026-33626 weaponized within 12h of disclosure). Daily 2026-10-23: evidence at 10/10 cap; verified Ollama SSRF CVE-2026-108836 (GHSA-fr42-jr2w-mx59, Moderate CVSS4 5.5, fixed 0.34.2) — noted but not added to evidence list. SGLang CVE-2026-86793 (SafeUnpickler bypass, CVSS 9.8, unauth RCE on /update_weights_from_tensor) and CVE-2026-15969 (same class, /load_lora_adapter_from_tensors) confirmed via secondary sources — queued pending GHSA primary verification; if confirmed, adds a 7th independent project (SGLang) to this trend. Forkast reports disclosure pace now ~1/week in Q3 2026 vs ~1/month in 2025. Weekly 2026-10-18: held at emerging (promoted only 13 days ago; two new Ollama GHSAs — critical unauth path traversal → RCE-as-root in Docker, and agent bash-approval bypass via prompt injection — keep velocity high but both land on one project and are GHSA-unreviewed; revisit for accelerating if a second org/project adds a critical next week). Weekly 2026-10-11: held at emerging (one new GHSA item). Promoted seed→emerging 2026-10-05: ≥6 independent orgs (Cyera, Sysdig, NVIDIA, Orca Security, GHSA maintainers, StingRAI) + concrete artifacts across the stack.
- evidence:
  - 2026-08-21 — https://github.com/advisories/GHSA-x2rj-828p-hx9m — Xinference CVE-2026-61539: unsafe eval() on Llama3 tool-call parser output → unauth RCE, CVSS 10.0, fixed v2.7.0.
  - 2026-08-24 — https://github.com/advisories/GHSA-x8qc-fggm-mpqg — Ollama CVE-2026-7482 "Bleeding Llama": crafted GGUF → heap OOB read → memory (env vars, API keys, system prompts) exfiltrated via /api/push. Floor 0.17.1.
  - 2026-08-24 — https://github.com/advisories/GHSA-3p4r-fq3f-q74v — llama.cpp CVE-2026-27940: GGUF heap overflow, bypass of the CVE-2025-53630 fix, public RCE PoC. Floor b8146.
  - 2026-08-07 — https://github.com/advisories/GHSA-6hc7-9rph-cm99 — llama.cpp CVE-2026-43631: UAF in llama-server sleep-idle vocab pointer, CVSS 9.2, unauth RCE; builds b7492–b9060.
  - (undated, accessed 2026-10-05) — https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models — Cyera discloses 10 llama.cpp vulnerabilities (2 UAFs CVSS 9.2, integer overflows, OOB); 5 unpatched as of Jun 2026.
  - 2026-04-22 — https://www.sysdig.com/blog/cve-2026-33626-how-attackers-exploited-lmdeploy-llm-inference-engines-in-12-hours — LMDeploy CVE-2026-33626 SSRF exploited in-the-wild within 12h31m of advisory; attacker port-scanned IMDS/internal services.
  - (undated, accessed 2026-10-05) — https://www.stingrai.io/blog/inference-server-security-vllm-triton-ollama-2026 — Roundup: NVIDIA Triton CVE-2026-24207 auth bypass CVSS 9.8 (fixed 26.03), vLLM CVE-2026-22778 RCE CVSS 9.8 (fixed 0.14.1), llama.cpp CVE-2026-33298.
  - 2026-06-16 — https://github.com/advisories?query=CVE-2026-41523 — vLLM CVE-2026-41523 (GHSA-q8gq-377p-jq3r, High): assert-based security check bypass in activation-function loading → arbitrary code execution via a malicious model; fixed version not stated on the opened page (0.22.0 per earlier secondary report).

  - 2026-09-29 — https://github.com/advisories/GHSA-44m8-pr79-3734 — Ollama CVE-2026-102697 (High, CVSS4 8.5, GHSA-unreviewed): experimental agent-mode Bash approval bypass — prompt-injected model output runs unapproved shell commands; fixed 0.31.2. Bridges runtime and agentic-injection.
  - 2026-10-08 — https://github.com/advisories/GHSA-w8p2-phwr-px3r — Ollama CVE-2026-103663 (Critical, CVSS4 9.4, GHSA-unreviewed): unauth path traversal in /api/pull writes outside the model store; RCE as root after restart in default Docker images; fixed 0.35.0 per advisory text (patched-versions field says unknown).

### id: agentic-injection-001 — Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)
- stage: emerging
- confidence: high
- last_evidence: 2026-10-22
- aliases: [tool poisoning, skill injection, memory injection, indirect prompt injection, IPI, hook poisoning, HookPry, AgentPhishing]
- notes: Attack surface spans agent subsystems — MCP tool descriptions, coding-agent skills, persistent agent memory, lifecycle hooks, email handling — plus a growing impossibility-result literature and defensive frameworks. Daily 2026-10-23: +1 evidence (AgentPhishing benchmark, fills slot 10/10); also opened Agent Mosaic (confidentiality leaks from cross-document aggregation), MPIDetector (multimodal PI detection reaching 99.8% on obfuscated injections), and AgentTriage (replayable security diagnosis across 5 agent runtimes) — 4 new independent groups in 2 days; strongest accelerating signal yet but stage move is a weekly decision. Weekly 2026-10-18: held at emerging; new evidence from independent groups (arXiv MCP capability-laundering at-scale study; Decepticon CVE on self-hosted ChatML token role forgery; Ollama agent-approval bypass cross-listed in local-inference-001) shows sustained flow into CVE/tool artifacts — strongest candidate for accelerating next week. Weekly 2026-10-11: held at emerging. Promoted seed→emerging 2026-10-05: ≥8 independent research groups + in-the-wild MCP tool-poisoning rates exceeding 60% reported.
- evidence:
  - 2026-03-23 — https://arxiv.org/abs/2603.22489 — STRIDE/DREAD threat model of the MCP stack; tool poisoning is the top client-side vulnerability; 5/7 major MCP clients lack static validation of tool descriptions.
  - 2026-08-22 — https://arxiv.org/abs/2608.21929 — SkillBloat: malicious coding-agent "skills" as a trusted instruction channel; token-amplification (resource-abuse) attacks reaching 5.4–10.1x average best amplification.
  - 2026-08-24 — https://arxiv.org/abs/2608.23471 — InjecMEM: single-interaction memory injection steers later retrieval-conditioned responses of LLM agents; retriever-agnostic anchor + adversarial command, transfers across backbones.
  - 2026-05-17 — https://arxiv.org/abs/2605.17634 — "AI Agents May Always Fall for Prompt Injections": impossibility result via Contextual Integrity theory; adversary can always construct a context making a blocked flow appear legitimate.
  - 2026-09-03 — https://arxiv.org/abs/2609.03884 — HookPry: attacker-controlled lifecycle-hook updates steer AI agent harnesses; 92.5% per-harness success rate across 7 harnesses; Microsoft Defender 0% detection.
  - 2026-10-02 — https://arxiv.org/abs/2610.03448 — PI detector re-evaluation: best detector on BIPIA catches only 2% of AgentDojo injections at 1% FPR; benchmark scores mislead deployment decisions.
  - 2026-09-24 — https://github.com/advisories/GHSA-g5f9-3xfg-p9mf — Decepticon CVE-2026-61732 (Critical, CVSS3 10.0, GitHub Reviewed): web-crawl output with ChatML special-token literals forges a higher-privileged role when the backend is self-hosted/OpenAI-compatible and preserves the tokens → command execution in sandbox; fixed 1.1.17.
  - 2026-10-18 — https://arxiv.org/abs/2610.22301 — "My Credentials, Please": at-scale detection of filesystem capability laundering in MCP servers (arXiv cs.CR listing 2026-10-18).
  - 2026-10-18 — https://arxiv.org/abs/2610.20776 — INFUSE: unified-surface benchmark for indirect prompt injection in agentic systems (arXiv cs.CR listing 2026-10-18).
  - 2026-10-22 — https://arxiv.org/abs/2610.31404 — AgentPhishing: adaptive phishing benchmark; 4/9 LLM email agents detect <10% of adapted attacks, >45% malicious-request compliance rate.

### id: ai-supplychain-001 — AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)
- stage: seed
- confidence: high
- last_evidence: 2026-10-18
- aliases: [nullifAI, FaceHugger, model poisoning, conjunctive poisoning, pickle deserialization, trust_remote_code bypass]
- notes: Weekly 2026-10-18: held at seed; one new paper (support-persistent backdoors for model reuse) — single source, not sustained; dormancy clock would start from 2026-10-18. Held at seed on 2026-10-11 (no new multi-org evidence since 2026-08-16; vLLM CVE-2026-41523 added as a bridge to local-inference-001). New trend seeded 2026-10-05. Attack surface spans model-hub poisoning (pickle/safetensors, malicious repos), library-level code execution bypasses (HF diffusers TOCTOU), deployment-artifact tampering (prompt wrappers + config metadata), and instruction backdoors in customized coding LLMs. Hugging Face breach (Jul 2026) demonstrated autonomous-agent exploitation of the model-hub attack surface at scale. ≥4 independent sources + concrete artifacts.
- evidence:
  - 2026-07-20 — https://www.helpnetsecurity.com/2026/07/20/hugging-face-breached-by-autonomous-ai-agent/ — Hugging Face breach: autonomous AI agent exploited dataset-loader + template-injection vulns → node-level access, cloud/cluster credential harvest, lateral movement across clusters.
  - 2026-07-27 — https://www.zafran.io/resources/facehugger-vulnerabilities-in-hugging-face-diffusers-open-door-to-supply-chain-attacks-on-enterprise-ai — FaceHugger: CVE-2026-44827/45804/44513 (CVSS 8.8/7.5) in HF diffusers; TOCTOU bypasses trust_remote_code → silent arbitrary code execution; fixed diffusers 0.38.0.
  - 2026-08-16 — https://arxiv.org/abs/2608.15913 — Conjunctive Poisoning: malicious deployment artifacts (prompt wrappers + metadata) deterministically alter model behavior without weight modification; existing defenses (PromptShield, SigStore) insufficient.
  - 2026-08-06 — https://arxiv.org/abs/2608.05659 — ARIA: automated instruction backdoor attacks on customized coding LLMs; 0.945 attack success rate, 1.000 false negative rate against detection mechanisms.
  - 2026-06-16 — https://github.com/advisories?query=CVE-2026-41523 — vLLM CVE-2026-41523: a malicious Hugging Face model triggers code execution via an assert-based check bypass at activation-function load; bridges inference-server and model-supply-chain surfaces.
  - 2026-10-18 — https://arxiv.org/abs/2610.21208 — "Clean Data Can Still Carry Backdoors": support-persistent backdoors that survive model reuse/fine-tuning (arXiv cs.CR listing 2026-10-18).

## observation_queue

<!--
Unverified or sub-bar items. Format:
- [queued YYYY-MM-DD] <what> — <why interesting> — <what is missing to promote>
Hard cap ~25 live items.
-->

- [resolved 2026-10-05] MCP tool poisoning / agentic prompt-injection cluster → absorbed into agentic-injection-001 with new evidence (HookPry, PI detector re-eval, impossibility result).
- [resolved 2026-10-05] Cyera "Bleeding Llama" research blog — opened and verified; exposure count (300k) unverifiable (no methodology); CVE data folded into local-inference-001.
- [resolved 2026-10-05] NVIDIA Triton CVE-2026-24207/-24209/-24210/-24215 — verified via StingRAI roundup (opened); folded into local-inference-001 evidence.
- [promoted 2026-10-05] Malicious models on Hugging Face / HF breach / FaceHugger → seed trend ai-supplychain-001.
- [dropped 2026-10-18] Hydra config-instantiation RCE (CVE-2026-68508) — 61 days old, no second independent ML-config-RCE source found in 2 weekly passes; re-queue if one appears.
- [dropped 2026-10-11] OWASP GenAI LLM Top 10 "2026" — canonical page genai.owasp.org/llm-top-10/ opened and lists only the 2025 edition (LLM01–LLM10:2025); secondary-source 2026 claims not corroborated. Re-queue only if a primary 2026 edition appears.
- [resolved 2026-10-11] vLLM CVE-2026-41523 — GHSA-q8gq-377p-jq3r opened and verified (published 2026-06-16, High); folded into local-inference-001 and ai-supplychain-001.
- [resolved 2026-10-11] PyRIT — Azure/PyRIT archived 2026-03-27 but banner points to https://github.com/microsoft/PyRIT, which is actively released (v1.0.0 24 Jul, v1.0.1 30 Jul, v1.1.0 4 Sep). Not a tooling gap; SOURCES.md updated.
- [resolved 2026-10-11] ExLlamaV3 — repo opened at github.com/turboderp-org/exllamav3 (EXL3 quant, CPU offload for MoE, spec decoding, TabbyAPI backend). The page does NOT state the 30–60% speed claim or an ExLlamaV2 succession; claim dropped as unverified. Added to study_shelf (axis 1b).
- [resolved 2026-10-18] Ollama MLX runtime — github.com/ollama/ollama/releases opened: v0.40.0 (2026-09-25) auto-runs MLX-supported architectures on Apple Silicon; releases through v0.40.6 (10-16). Apple-only, irrelevant to the RTX 4070 Ti envelope; no ledger action.
- [resolved 2026-10-18] Unsloth MoE fine-tuning — github.com/unslothai/unsloth/releases opened: v0.1.904/905 claim QLoRA 4.1x (Qwen3.5-35B-A3B) / 3.3x (Qwen3-30B-A3B) speedups, measured on A100/RTX PRO 6000 (datacenter — flag, not 12GB-feasible for 30B+ MoE); gpt-oss-20b QLoRA 2–3x (v0.1.903); no independent benchmarks. Added to study_shelf.
- [dropped 2026-10-18] ACM WPLL 2026 reasoning-prompt jailbreak-defense paper — primary page not located in 2 weekly passes; re-queue only with a URL.
- [queued 2026-10-18, partially verified 2026-10-23] Self-hosted LLM front-end/gateway app-layer advisories — ChatOllama CVE-2026-111702 / GHSA-7pf8-cp62-gc3p (High, CVSS4 8.7, IDOR exposing private knowledge bases, opened 2026-10-23), Open WebUI CVE-2026-109296 (Medium, missing authz for disabled backends, confirmed via secondary), Portkey AI Gateway CVE-2026-110719 (SSRF, confirmed via Debian tracker), Langflow SSRF GHSA-j8f7-x8jm-wmm4, 9router DNS-rebinding CVE-2026-56676 — candidate new trend (app-layer of the local stack) — missing: open Open WebUI/Portkey/Langflow/9router GHSAs as primaries; need ≥3 independent orgs for trend bar.
- [resolved 2026-10-23] "Decision models" — Ollama v0.40.7 adds pplx-decider (27B, Perplexity), v0.40.9 adds d3 decision models (2B–27B); confirmed in release notes opened this session. Feature/tooling item, no security angle found; no ledger action.
- [resolved 2026-10-23] Ollama GHSA-fr42-jr2w-mx59 / CVE-2026-108836 (Moderate, CVSS4 5.5, SSRF in IsValid/Pull API, fixed 0.34.2) — opened and verified; noted in local-inference-001 notes (evidence at 10/10 cap).
- [queued 2026-10-23] SGLang CVE-2026-86793 (CVSS 9.8) + CVE-2026-15969 — SafeUnpickler denylist bypass → unauth RCE via pickle deserialization on /update_weights_from_tensor and /load_lora_adapter_from_tensors when no API key set; no vendor patch at disclosure (Sep 2026). Confirmed via opencve.io, mend.io, Forkast analysis — missing: open GHSA primary (GHSA-2wvm-gjg7-5jfm returned 404). If verified, adds SGLang as 7th project to local-inference-001.
- [queued 2026-10-23] DeepSeek Harness CVE-2026-82533 (CVSS 9.4) — unauthenticated local API lets agent disable its own sandbox from inside container; described as "first confirmed agent runtime sandbox escape" (Forkast, secondary) — missing: open GHSA/NVD primary.
- [queued 2026-10-23] NemoClaw CVE-2026-65105 (CVSS 8.1) — NVIDIA NemoClaw launched Ollama on 0.0.0.0 without auth → DNS-rebinding → persistent model chat-template poisoning; patched Aug 2026 per CSA/eSecurity (secondary) — missing: open NVIDIA security bulletin as primary.
- [queued 2026-10-23] Inference-server disclosure pace acceleration — Forkast reports ~1 critical CVE/week in Q3 2026 vs ~1/month in 2025 across SGLang, Ollama, Langflow, DeepSeek Harness — cross-cutting signal for local-inference-001 stage assessment. Secondary source, not evidence.

## study_shelf

<!--
0–2 picks per daily run, newest first. Format:
- [Title](primary URL) — source (YYYY-MM-DD): one line on why it matters.
Prune picks older than 30 days on weekly runs.
-->

- [AgentTriage: Replayable Security Diagnosis Across Heterogeneous Agent Runtimes](https://arxiv.org/abs/2610.30738) — Jie Ying et al. (2026-10-22): contract-based framework for grounded security claims across 5 agent runtimes, 0.858 diagnosis score, open-source; directly applicable to local agent setups.
- [Unsloth v0.1.909-beta: DeepSeek-V4.1 & multi-GPU training](https://github.com/unslothai/unsloth/releases) — unslothai (2026-10-19): DeepSeek-V4.1-Flash-1017 (552B/16B-active, ~125GB at 1-bit with Engram on SSD), FSDP2 multi-GPU LoRA/QLoRA alpha, one-command MCP setup (`unsloth mcp add`). Core axis-1b tool; multi-GPU training democratizes fine-tuning beyond single-card.
- [Unsloth releases (v0.1.904–0.1.908)](https://github.com/unslothai/unsloth/releases) — unslothai (2026-10-15): fast-moving local fine-tune + inference studio — OS-level sandboxing for model-run code, browser-use for local models, QLoRA MoE speedups (measured on datacenter GPUs; independent benchmarks absent). Core axis-1b tool.
- [ExLlamaV3](https://github.com/turboderp-org/exllamav3) — turboderp-org (accessed 2026-10-11): EXL3 quantization + inference library for consumer GPUs with MoE CPU offload, speculative decoding and TabbyAPI backend; the natural fit for a 12GB RTX 4070 Ti (axis 1b). Performance claims unverified.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): systematic audit of the most widely-used local inference engine; 5 of 10 bugs unpatched — essential reading for anyone running llama.cpp in production or red-teaming local deployments.

## strategy_notes

<!--
Dated notes from the curator or radar-adopted scope amendments.
-->

- 2026-08-24 — repo initialized by curator; scope seeded per AGENTS.md (local-model stack first).
- 2026-08-24 — CURATOR directive: add scope axis 1b (AI-driven solution engineering stack).
  Track practical build-stack news (fine-tuning frameworks, consumer-GPU inference,
  quantization, RAG/agent tooling, ≤8B model releases), not only bleeding-edge security.
  Hardware relevance filter: curator workstation = RTX 4070 Ti, 12GB VRAM — prioritize
  what fits that envelope; flag datacenter-only items instead of dropping them.

- 2026-10-04 — radar-adopted: anchoring check N/A this week (no new evidence except Triton, which landed on a pre-existing trend). Next week's exploration should prioritize taxonomy/supply-chain axes (HF malicious models, OWASP 2026) and the 1b engineering stack, which has zero ledger coverage.
- 2026-10-11 — radar-adopted: ANCHORING WARNING — all evidence added this week (vLLM GHSA) landed on pre-existing trends, and no daily sweep ran 10-06..10-11. Next week: explore taxonomies (MITRE ATLAS, real OWASP updates), 1b engineering stack primaries (Unsloth, llama.cpp quant/KV-cache work), and vendor blogs, which have not been opened in any logged run.
- 2026-10-18 — radar-adopted: ANCHORING WARNING (3rd week) — all new evidence landed on pre-existing trends; 0/7 daily slots ran again. This week's weekly-run exploration surfaced a candidate new trend (app-layer advisories in self-hosted LLM front-ends/gateways, queued). Next week: verify that cluster, open ATLAS/vendor-blog sources, and sweep 1b primaries (llama.cpp quant/KV-cache).

## blockers

<!--
Access/tooling blockers that prevented verification. Format:
- [YYYY-MM-DD] <what is blocked> — <what was tried> — <status>
-->

- [2026-08-25] State persistence across scheduled sessions — session sandbox started empty (repo absent at /mnt/agents/output); recovered by cloning the GitHub remote during a curator-granted public window. Future scheduled runs CANNOT re-clone once the repo is private again (no credentials persist across sessions) — status: OPEN, curator must either keep the repo clone present in the persistent mount, provide a credential that survives sessions, or accept that each run restores from GitHub manually. Escalated per Hard rules → Operator notifications.
- [2026-10-04] Daily routine not executed since 2026-08-25 (40 days; zero entries in reports/ or logs/source_rotation.md since) — weekly run found no daily reports for W40; all swept-list coverage this week = 0/N. Cause unknown (scheduler stopped or sandbox restore failure per the OPEN blocker above). Status: OPEN, escalated to curator via notification.
- [2026-08-25] r/LocalLLaMA (reddit.com) — JSON endpoint rejected again, 2nd consecutive run — degraded; community-pulse lane uncovered.
- [2026-10-05] NVIDIA security bulletin (nvidia.custhelp.com) — returned HTTP 403; Triton CVE details verified via secondary roundup (stingrai.io) instead. Non-blocking.
- [2026-10-05] Microsoft "State of MCP Security 2026" blog (techcommunity.microsoft.com) — page returned empty content; topic covered via independent sources. Non-blocking.
- [2026-10-05] GitHub MCP scoped to radar repo only — cannot query external repos for releases via API; used WebFetch on GitHub release pages instead. Non-blocking.
- [2026-10-05] 41-day gap since last scan (2026-08-25 → 2026-10-05) — scheduled runs did not fire or did not persist. Root cause likely the state-persistence blocker above. Status: OPEN.
- [2026-10-18] Daily sweeps absent for ALL of W42 (last daily 2026-10-05; 13 days, 0 entries in reports/ or logs/source_rotation.md) — third consecutive weekly with no/near-zero daily coverage; escalated to curator via notification. Weekly run itself had working web access (GitHub, arXiv opened). Status: OPEN. Update 2026-10-23: daily run executed successfully (W43).
- [2026-10-11] Daily sweeps absent 10-06..10-11 (only 2026-10-05 ran in W41). Vendor/lab blog feeds (all 10 in SOURCES primary list) never logged as opened or degraded. Status: OPEN.
