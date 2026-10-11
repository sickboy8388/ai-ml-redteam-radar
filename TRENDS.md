# AI-ML-RedTeam Radar — Trend ledger

Single source of truth. The README and reports are derived from this file.
Last updated: 2026-10-11 (daily)

Trend stages: `seed` → `emerging` → `accelerating` → `mainstreaming` → `dormant`.
Evidence line format: `date — primary URL — one line of context`. Max 10 per trend.

---

## trends

### id: local-inference-001 — Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)
- stage: emerging
- confidence: high
- last_evidence: 2026-10-05
- aliases: [Bleeding Llama, Breaking Local AI Runtimes]
- notes: Critical CVE cluster spanning the entire local/self-hosted inference stack (llama.cpp, Ollama, vLLM, LMDeploy, NVIDIA Triton, Xinference, SGLang); attack classes include GGUF parser overflows, server use-after-free, SSRF via multimodal endpoints, Jinja2 SSTI via model chat templates, and authentication bypass. In-the-wild exploitation confirmed (LMDeploy CVE-2026-33626 weaponized within 12h of disclosure). Daily 2026-10-11: held at emerging; added SGLang CVE-2026-5760 (gap fill from Apr 2026, CVSS 9.8). Weekly 2026-10-11: held at emerging. Promoted seed→emerging 2026-10-05.
- evidence:
  - 2026-08-21 — https://github.com/advisories/GHSA-x2rj-828p-hx9m — Xinference CVE-2026-61539: unsafe eval() on Llama3 tool-call parser output → unauth RCE, CVSS 10.0, fixed v2.7.0.
  - 2026-08-24 — https://github.com/advisories/GHSA-x8qc-fggm-mpqg — Ollama CVE-2026-7482 "Bleeding Llama": crafted GGUF → heap OOB read → memory (env vars, API keys, system prompts) exfiltrated via /api/push. Floor 0.17.1.
  - 2026-08-24 — https://github.com/advisories/GHSA-3p4r-fq3f-q74v — llama.cpp CVE-2026-27940: GGUF heap overflow, bypass of the CVE-2025-53630 fix, public RCE PoC. Floor b8146.
  - 2026-08-07 — https://github.com/advisories/GHSA-6hc7-9rph-cm99 — llama.cpp CVE-2026-43631: UAF in llama-server sleep-idle vocab pointer, CVSS 9.2, unauth RCE; builds b7492–b9060.
  - (undated, accessed 2026-10-05) — https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models — Cyera discloses 10 llama.cpp vulnerabilities (2 UAFs CVSS 9.2, integer overflows, OOB); 5 unpatched as of Jun 2026.
  - 2026-04-22 — https://www.sysdig.com/blog/cve-2026-33626-how-attackers-exploited-lmdeploy-llm-inference-engines-in-12-hours — LMDeploy CVE-2026-33626 SSRF exploited in-the-wild within 12h31m of advisory; attacker port-scanned IMDS/internal services.
  - (undated, accessed 2026-10-05) — https://www.stingrai.io/blog/inference-server-security-vllm-triton-ollama-2026 — Roundup: NVIDIA Triton CVE-2026-24207 auth bypass CVSS 9.8 (fixed 26.03), vLLM CVE-2026-22778 RCE CVSS 9.8 (fixed 0.14.1), llama.cpp CVE-2026-33298.
  - 2026-05-05 — https://www.cyera.com/research/bleeding-llama-critical-unauthenticated-memory-leak-in-ollama — Cyera: ~300k exposed Ollama servers; CVE-2026-7482 exfiltrates API keys/prompts via crafted GGUF + /api/push; no methodology for server count disclosed.
  - 2026-06-16 — https://github.com/advisories?query=CVE-2026-41523 — vLLM CVE-2026-41523 (GHSA-q8gq-377p-jq3r, High): assert-based security check bypass in activation-function loading → arbitrary code execution via a malicious model; fixed version not stated on the opened page (0.22.0 per earlier secondary report).
  - 2026-04-20 — https://labs.cloudsecurityalliance.org/research/csa-research-note-sglang-cve-2026-5760-gguf-rce-20260422-csa/ — SGLang CVE-2026-5760: Jinja2 SSTI via GGUF chat_template in /v1/rerank → unauth RCE, CVSS 9.8; no official patch at disclosure (CERT/CC VU#915947).

### id: agentic-injection-001 — Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)
- stage: emerging
- confidence: high
- last_evidence: 2026-10-08
- aliases: [tool poisoning, skill injection, memory injection, indirect prompt injection, IPI, hook poisoning, HookPry, PyCache Trap]
- notes: Attack surface spans agent subsystems — MCP tool descriptions, coding-agent skills, persistent agent memory, lifecycle hooks, bytecode-cache substitution in skill packages — plus a growing impossibility-result literature and defensive frameworks. Daily 2026-10-11: +2 evidence (NOMOS compiled tool-call gates, PyCache Trap skill scanner bypass); held at emerging. Promoted seed→emerging 2026-10-05.
- evidence:
  - 2026-03-23 — https://arxiv.org/abs/2603.22489 — STRIDE/DREAD threat model of the MCP stack; tool poisoning is the top client-side vulnerability; 5/7 major MCP clients lack static validation of tool descriptions.
  - 2026-08-22 — https://arxiv.org/abs/2608.21929 — SkillBloat: malicious coding-agent "skills" as a trusted instruction channel; token-amplification (resource-abuse) attacks reaching 5.4–10.1x average best amplification.
  - 2026-08-23 — https://arxiv.org/abs/2608.22248 — AEGIS: instruction/data separation via latent instruction manifolds; multi-layer consensus detector for indirect prompt injection with lower over-refusal.
  - 2026-08-24 — https://arxiv.org/abs/2608.23471 — InjecMEM: single-interaction memory injection steers later retrieval-conditioned responses of LLM agents; retriever-agnostic anchor + adversarial command, transfers across backbones.
  - 2026-08-24 — https://arxiv.org/abs/2608.22868 — AgentFlow: flow-centric policy language + runtime reference monitor; on 949 AgentDojo injected cases cuts confirmed compromise 33.0%→0.0% while raising utility.
  - 2026-05-17 — https://arxiv.org/abs/2605.17634 — "AI Agents May Always Fall for Prompt Injections": impossibility result via Contextual Integrity theory; adversary can always construct a context making a blocked flow appear legitimate.
  - 2026-09-03 — https://arxiv.org/abs/2609.03884 — HookPry: attacker-controlled lifecycle-hook updates steer AI agent harnesses; 92.5% per-harness success rate across 7 harnesses; Microsoft Defender 0% detection.
  - 2026-10-02 — https://arxiv.org/abs/2610.03448 — PI detector re-evaluation: best detector on BIPIA catches only 2% of AgentDojo injections at 1% FPR; benchmark scores mislead deployment decisions.
  - 2026-10-08 — https://arxiv.org/abs/2610.11030 — NOMOS: compiles natural-language policies into statically verified tool-call gates; 0% ASR on AgentDojo banking, microsecond decisions without LLM calls.
  - 2026-10-07 — https://arxiv.org/abs/2610.10612 — PyCache Trap: bytecode-cache substitution bypasses 7 agent skill scanners at 94–100% success; proposes execution-aware validation (EAV) countermeasure.

### id: ai-supplychain-001 — AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)
- stage: seed
- confidence: high
- last_evidence: 2026-10-07
- aliases: [nullifAI, FaceHugger, model poisoning, conjunctive poisoning, pickle deserialization, trust_remote_code bypass, DITTO]
- notes: Daily 2026-10-11: +1 evidence (DITTO pickle scanner; 9.3% of top HF repos still use unsafe pickle); held at seed (6 evidence, 5 orgs — approaching emerging bar but no in-the-wild incident cluster yet). Attack surface spans model-hub poisoning (pickle/safetensors, malicious repos), library-level code execution bypasses (HF diffusers TOCTOU), deployment-artifact tampering (prompt wrappers + config metadata), instruction backdoors in customized coding LLMs, and inference-server model-loading code execution. Hugging Face breach (Jul 2026) demonstrated autonomous-agent exploitation of the model-hub attack surface at scale.
- evidence:
  - 2026-07-20 — https://www.helpnetsecurity.com/2026/07/20/hugging-face-breached-by-autonomous-ai-agent/ — Hugging Face breach: autonomous AI agent exploited dataset-loader + template-injection vulns → node-level access, cloud/cluster credential harvest, lateral movement across clusters.
  - 2026-07-27 — https://www.zafran.io/resources/facehugger-vulnerabilities-in-hugging-face-diffusers-open-door-to-supply-chain-attacks-on-enterprise-ai — FaceHugger: CVE-2026-44827/45804/44513 (CVSS 8.8/7.5) in HF diffusers; TOCTOU bypasses trust_remote_code → silent arbitrary code execution; fixed diffusers 0.38.0.
  - 2026-08-16 — https://arxiv.org/abs/2608.15913 — Conjunctive Poisoning: malicious deployment artifacts (prompt wrappers + metadata) deterministically alter model behavior without weight modification; existing defenses (PromptShield, SigStore) insufficient.
  - 2026-08-06 — https://arxiv.org/abs/2608.05659 — ARIA: automated instruction backdoor attacks on customized coding LLMs; 0.945 attack success rate, 1.000 false negative rate against detection mechanisms.
  - 2026-06-16 — https://github.com/advisories?query=CVE-2026-41523 — vLLM CVE-2026-41523: a malicious Hugging Face model triggers code execution via an assert-based check bypass at activation-function load; bridges inference-server and model-supply-chain surfaces.
  - 2026-10-07 — https://arxiv.org/abs/2610.10735 — DITTO: context-aware pickle scanner benchmarked on 10k+ HF repos; 9.3% still use unsafe pickle format; 100% detection, 0.7% FPR on PickleBench (959 benign + 92 malicious models).

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
- [re-dated 2026-10-11] Hydra config-instantiation RCE — CVE-2026-68508 / GHSA-2cp2-2r3c-7p7r verified via GitHub Advisory Database (published 2026-08-21): `hydra.utils.instantiate` with untrusted config → code execution; widely used for ML experiment configs — missing: ≥2 more independent sources on ML-pipeline config-RCE to seed a trend (none found; stale 47 days — drop at next weekly if still none).
- [dropped 2026-10-11] OWASP GenAI LLM Top 10 "2026" — canonical page genai.owasp.org/llm-top-10/ opened and lists only the 2025 edition (LLM01–LLM10:2025); secondary-source 2026 claims not corroborated. Re-queue only if a primary 2026 edition appears.
- [resolved 2026-10-11] vLLM CVE-2026-41523 — GHSA-q8gq-377p-jq3r opened and verified (published 2026-06-16, High); folded into local-inference-001 and ai-supplychain-001.
- [resolved 2026-10-11] PyRIT — Azure/PyRIT archived 2026-03-27 but banner points to https://github.com/microsoft/PyRIT, which is actively released (v1.0.0 24 Jul, v1.0.1 30 Jul, v1.1.0 4 Sep). Not a tooling gap; SOURCES.md updated.
- [resolved 2026-10-11] ExLlamaV3 — repo opened at github.com/turboderp-org/exllamav3 (EXL3 quant, CPU offload for MoE, spec decoding, TabbyAPI backend). The page does NOT state the 30–60% speed claim or an ExLlamaV2 succession; claim dropped as unverified. Added to study_shelf (axis 1b).
- [resolved 2026-10-11] Ollama v0.40.0-rc3 MLX runtime → confirmed: v0.40.3 stable released 2026-10-11; v0.40.x adds background model upgrades, cloud model proxying; MLX support for Apple Silicon confirmed.
- [queued 2026-10-05, primary opened 2026-10-11] Unsloth MoE fine-tuning — Substack primary (Feb 10, 2026): up to 12x faster MoE training, 35% less VRAM, embedding model support; gpt-oss-20b in 12.8GB VRAM claimed. Self-reported benchmarks only — missing: independent validation of speedup claims.
- [re-dated 2026-10-11] ACM WPLL 2026 paper: inference-time jailbreak defenses consistently bypassed by long reasoning-heavy prompts (open-source models incl. Llama 3.2, Mistral, Qwen, Gemma) — missing: open the paper page.
- [queued 2026-10-11] Speedbumps (arXiv:2610.10929, Oct 7): adversarial rejection attacks on speculative decoding degrade LLM inference to slower-than-autoregressive; suffixes transfer across drafters/targets — missing: real-world impact assessment, vendor response. Relevant to local inference cost/availability.
- [queued 2026-10-11] BRANCH (arXiv:2610.10742, Oct 7): branching tree-search bypass of multi-scanner AI guardrails; 100% ASR across 6 guardrail systems, transfers to 29 unseen including 8 commercial — missing: vendor responses, deployment impact data.
- [queued 2026-10-11] RAG Security Meta-Model (arXiv:2610.11893, Oct 8): structured catalog of RAG threats/mitigations from 43 publications; web visualizer; coverage gaps at output integrity — missing: peer review, adoption signals.
- [queued 2026-10-11] Agent Security Incidents / PASAC (arXiv:2610.12463, Oct 8): comparative case study of 2026 agent security incidents at OpenAI, Anthropic, Google; five-layer Boundary Assurance Stack — missing: peer review, Gemini mechanism still provisional.

## study_shelf

<!--
0–2 picks per daily run, newest first. Format:
- [Title](primary URL) — source (YYYY-MM-DD): one line on why it matters.
Prune picks older than 30 days on weekly runs.
-->

- [DITTO: Context-aware Pickle-based Pre-Trained Model Scanner](https://arxiv.org/abs/2610.10735) — arXiv (2026-10-07): practical scanner for auditing pickle-serialized models on HuggingFace; 9.3% of top repos still use unsafe pickle; 100% detection at 0.7% FPR. Essential tool for model supply-chain audits.
- [ExLlamaV3 v1.6.1](https://github.com/turboderp-org/exllamav3/releases) — turboderp-org (2026-10-10): very active development — v1.6.1 adds recurrent draft models, lower VRAM drafting overhead, ROCm support (v1.6.0), token-embedding quantization (v1.5.4); natural fit for 12GB RTX 4070 Ti (axis 1b).
- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): lifecycle hooks in agent harnesses are a blindspot — 92.5% compromise rate across 7 harnesses, 0% detection. Directly relevant when assessing local agent setups with plugin/hook systems.
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
- [2026-10-11] Daily sweeps absent 10-06..10-10 (only 2026-10-05 and 2026-10-11 ran in W41). Vendor/lab blog feeds not individually opened (web search triage found no October posts on protectai, hiddenlayer, lakera). Status: PARTIALLY RESOLVED (daily run 2026-10-11 completed full sweep).
- [2026-10-11] r/LocalLLaMA — degraded 4th consecutive run (reddit.com JSON endpoint inaccessible). Community-pulse lane uncovered.
