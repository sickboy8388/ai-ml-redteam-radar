# AI-ML-RedTeam Radar — Trend ledger

Single source of truth. The README and reports are derived from this file.
Last updated: 2026-10-15

Trend stages: `seed` → `emerging` → `accelerating` → `mainstreaming` → `dormant`.
Evidence line format: `date — primary URL — one line of context`. Max 10 per trend.

---

## trends

### id: local-inference-001 — Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)
- stage: emerging
- confidence: high
- last_evidence: 2026-10-15
- aliases: [Bleeding Llama, Breaking Local AI Runtimes]
- notes: Critical CVE cluster spanning the entire local/self-hosted inference stack (llama.cpp, Ollama, vLLM, LMDeploy, NVIDIA Triton, Xinference); attack classes include GGUF parser overflows, server use-after-free, SSRF via multimodal endpoints, authentication bypass, and cross-user data leaks. In-the-wild exploitation confirmed (LMDeploy CVE-2026-33626 weaponized within 12h of disclosure). Daily 2026-10-15: held at emerging; added vLLM cross-user data leak (new confidentiality attack class); 10/10 evidence slots full. Weekly 2026-10-11: held at emerging (one new GHSA item, no sustained acceleration). Promoted seed→emerging 2026-10-05: ≥6 independent orgs (Cyera, Sysdig, NVIDIA, Orca Security, GHSA maintainers, StingRAI) + concrete artifacts across the stack.
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
  - 2026-09-08 — https://github.com/advisories/GHSA-7m6h-x95x-82q5 — vLLM CVE-2026-73558: integer overflow in act_and_mul_kernel → cross-user data leak in inference batches (attacker in same batch receives victim's output), CVSS 5.3; fixed v0.27.0.

### id: agentic-injection-001 — Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)
- stage: accelerating
- confidence: high
- last_evidence: 2026-10-06
- aliases: [tool poisoning, skill injection, memory injection, indirect prompt injection, IPI, hook poisoning, HookPry, ChatML injection, Decepticon]
- notes: Attack surface spans agent subsystems — MCP tool descriptions, MCP OAuth protocol, coding-agent skills, persistent agent memory, lifecycle hooks, ChatML token injection in web crawl — plus a growing impossibility-result literature and defensive frameworks. Daily 2026-10-15: promoted emerging→accelerating on 2 new critical CVEs (Decepticon ChatML injection CVSS 10.0, MCP SDK OAuth credential theft CVSS 7.5) + 4 new independent October papers (Kairos, BrowseSafe++, TRAP, AgentSafeEvo) from 6 independent orgs; concrete exploitation artifacts now span tool descriptions, hooks, memory, skills, web crawl content, and protocol-level OAuth. Weekly 2026-10-11: held at emerging (no new evidence that week). Promoted seed→emerging 2026-10-05: ≥8 independent research groups + in-the-wild MCP tool-poisoning rates exceeding 60% reported.
- evidence:
  - 2026-03-23 — https://arxiv.org/abs/2603.22489 — STRIDE/DREAD threat model of the MCP stack; tool poisoning is the top client-side vulnerability; 5/7 major MCP clients lack static validation of tool descriptions.
  - 2026-08-22 — https://arxiv.org/abs/2608.21929 — SkillBloat: malicious coding-agent "skills" as a trusted instruction channel; token-amplification (resource-abuse) attacks reaching 5.4–10.1x average best amplification.
  - 2026-08-23 — https://arxiv.org/abs/2608.22248 — AEGIS: instruction/data separation via latent instruction manifolds; multi-layer consensus detector for indirect prompt injection with lower over-refusal.
  - 2026-08-24 — https://arxiv.org/abs/2608.23471 — InjecMEM: single-interaction memory injection steers later retrieval-conditioned responses of LLM agents; retriever-agnostic anchor + adversarial command, transfers across backbones.
  - 2026-08-24 — https://arxiv.org/abs/2608.22868 — AgentFlow: flow-centric policy language + runtime reference monitor; on 949 AgentDojo injected cases cuts confirmed compromise 33.0%→0.0% while raising utility.
  - 2026-05-17 — https://arxiv.org/abs/2605.17634 — "AI Agents May Always Fall for Prompt Injections": impossibility result via Contextual Integrity theory; adversary can always construct a context making a blocked flow appear legitimate.
  - 2026-09-03 — https://arxiv.org/abs/2609.03884 — HookPry: attacker-controlled lifecycle-hook updates steer AI agent harnesses; 92.5% per-harness success rate across 7 harnesses; Microsoft Defender 0% detection.
  - 2026-10-02 — https://arxiv.org/abs/2610.03448 — PI detector re-evaluation: best detector on BIPIA catches only 2% of AgentDojo injections at 1% FPR; benchmark scores mislead deployment decisions.
  - 2026-09-24 — https://github.com/advisories/GHSA-g5f9-3xfg-p9mf — Decepticon CVE-2026-61732: ChatML special-token injection in web crawl output → role-boundary forgery + arbitrary command execution in agent sandbox, CVSS 10.0; affects BYOK agents on vLLM/Ollama/LM Studio backends; fixed v1.1.17.
  - 2026-10-06 — https://github.com/advisories/GHSA-6qxp-vccf-f47h — MCP TypeScript SDK CVE-2026-104850: OAuth client sends credentials to server-chosen authorization endpoint → token/secret theft without user interaction, CVSS 7.5; fixed @modelcontextprotocol/sdk 1.31.0, @modelcontextprotocol/client 2.2.0.

### id: ai-supplychain-001 — AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)
- stage: seed
- confidence: high
- last_evidence: 2026-10-15
- aliases: [nullifAI, FaceHugger, model poisoning, conjunctive poisoning, pickle deserialization, trust_remote_code bypass]
- notes: Daily 2026-10-15: added LMDeploy pickle-deserialization RCE (CVSS 9.8) as 6th evidence item — inference-server internal comms using pickle on unauthenticated ZMQ sockets; held at seed (still 4 independent orgs, no 3rd-org surge). Held at seed on 2026-10-11 (no new multi-org evidence since 2026-08-16; vLLM CVE-2026-41523 added as a bridge to local-inference-001). New trend seeded 2026-10-05. Attack surface spans model-hub poisoning (pickle/safetensors, malicious repos), library-level code execution bypasses (HF diffusers TOCTOU), deployment-artifact tampering (prompt wrappers + config metadata), instruction backdoors in customized coding LLMs, and pickle deserialization in inference-server internal transports. Hugging Face breach (Jul 2026) demonstrated autonomous-agent exploitation of the model-hub attack surface at scale. ≥4 independent sources + concrete artifacts.
- evidence:
  - 2026-07-20 — https://www.helpnetsecurity.com/2026/07/20/hugging-face-breached-by-autonomous-ai-agent/ — Hugging Face breach: autonomous AI agent exploited dataset-loader + template-injection vulns → node-level access, cloud/cluster credential harvest, lateral movement across clusters.
  - 2026-07-27 — https://www.zafran.io/resources/facehugger-vulnerabilities-in-hugging-face-diffusers-open-door-to-supply-chain-attacks-on-enterprise-ai — FaceHugger: CVE-2026-44827/45804/44513 (CVSS 8.8/7.5) in HF diffusers; TOCTOU bypasses trust_remote_code → silent arbitrary code execution; fixed diffusers 0.38.0.
  - 2026-08-16 — https://arxiv.org/abs/2608.15913 — Conjunctive Poisoning: malicious deployment artifacts (prompt wrappers + metadata) deterministically alter model behavior without weight modification; existing defenses (PromptShield, SigStore) insufficient.
  - 2026-08-06 — https://arxiv.org/abs/2608.05659 — ARIA: automated instruction backdoor attacks on customized coding LLMs; 0.945 attack success rate, 1.000 false negative rate against detection mechanisms.
  - 2026-06-16 — https://github.com/advisories?query=CVE-2026-41523 — vLLM CVE-2026-41523: a malicious Hugging Face model triggers code execution via an assert-based check bypass at activation-function load; bridges inference-server and model-supply-chain surfaces.
  - 2026-09-18 — https://github.com/advisories/GHSA-2vh9-42vm-xmv2 — LMDeploy CVE-2025-66455: pickle deserialization via ZMQ recv_pyobj() in DistServe control plane → unauth RCE (CVSS 9.8); attacker reaches the endpoint via unauthenticated POST /distserve/p2p_connect; fixed v0.16.0.

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
- [resolved 2026-10-15] Ollama v0.40.0-rc3 MLX runtime → Ollama v0.40.4 now stable (Oct 12) with decision models, MLX runner on Apple Silicon, multimodal embeddings, speculative decoding improvements. No security-specific changes noted in release notes.
- [queued 2026-10-05] Unsloth MoE fine-tuning — Feb 2026 release claims 7–12x speedup on MoE fine-tuning, native Llama 4 QLoRA, 500+ base models — relevant to scope axis 1b — missing: open Unsloth release/blog primary (secondary guides describe v0.1.512-beta Jul 2026).
- [re-dated 2026-10-15] ACM WPLL 2026 paper: inference-time jailbreak defenses consistently bypassed by long reasoning-heavy prompts (open-source models incl. Llama 3.2, Mistral, Qwen, Gemma) — missing: open the paper page. Stale 2+ runs.
- [dropped 2026-10-15] Hydra config-instantiation RCE (CVE-2026-68508) — stale 55 days, no additional independent sources found in 3 sweeps. Drop per weekly guidance.
- [queued 2026-10-15] Langflow critical CVE cluster (Oct 5–7): CVE-2026-105697 MCP stdio command injection CVSS 9.9, CVE-2026-10561 unsandboxed Python RCE, CVE-2026-8505 webhook auth bypass, CVE-2026-9205 weak Fernet key — 4 critical CVEs in agent orchestration framework; GHSA-w794-rj3p-xv45 opened and verified. Potential evidence for agentic-injection-001 (MCP vector) or new agent-framework-RCE cluster — missing: ≥2 more independent agent-framework CVE clusters to seed a trend.
- [queued 2026-10-15] PraisonAI critical CVE cluster (Oct 7–8): CVE-2026-61445 arbitrary file write via LLM tool calls, CVE-2026-61447 unsandboxed LLM code execution leaking env secrets (CVSS 10.0), CVE-2026-62176 f-string code injection — GHSA-2xv2-w8cq-5gxw opened and verified. Agent frameworks running LLM output without sandboxing.
- [queued 2026-10-15] OWASP GenAI LLM Top 10 2026 — confirmed published Aug 3 2026 (opened genai.owasp.org primary). Prompt Injection is LLM01:2026; includes Hidden Context Exposure (LLM08), Vector/Embedding Weaknesses (LLM09). Excessive Agency now #3. Could seed a taxonomies trend with MITRE ATLAS update — missing: full item list (download required) + 3rd independent taxonomy update.
- [queued 2026-10-15] MITRE ATLAS v2026.09 (Sep 15 2026) — reported 120 techniques, 88 sub-techniques, 73 case studies; agentic AI platform tags on 139/208 entries; ATLAS navigator data v1.14.0 (Feb 2026, ATLAS Data 5.4.0) opened on GitHub. Secondary sources only for Sep release — missing: open MITRE ATLAS primary changelog.
- [queued 2026-10-15] NLTK CVE-2026-79657 (GHSA-x99w-6fgc-pmfw, Sep 8): allowlisted pickle loaders in NLTK still permit code execution — ML pipeline supply-chain angle — missing: open the individual advisory page.
- [queued 2026-10-15] LMDeploy CVE-2025-59953 (GHSA-5h8j-6crg-7rmw, Sep 16): second pickle-deserialization RCE via zmq_rpc.call_and_response() — companion to CVE-2025-66455 already in ai-supplychain-001 evidence — missing: open individual advisory.

## study_shelf

<!--
0–2 picks per daily run, newest first. Format:
- [Title](primary URL) — source (YYYY-MM-DD): one line on why it matters.
Prune picks older than 30 days on weekly runs.
-->

- [Kairos: Transactional Security Enforcement at the System Boundary for LLM Agents](https://arxiv.org/abs/2610.18457) — arXiv (2026-10-13): reference monitor for opaque agents; defers ambiguous effects and uses bounded oracles to decide; reduces AgentDojo attack success 47.0%→2.7% without utility loss. Practical defense pattern for local agent deployments.
- [TRAP: Tree-Guided Reinforcement-Augmented Probing for Automated LLM Jailbreaking](https://arxiv.org/abs/2610.17313) — arXiv (2026-10-12): hierarchical RL framework for black-box automated jailbreaking; organizes strategies in a semantic tree, persists preferences across objectives; 45.6–97.9% ASR on 7 aligned models. Useful for red-team automation tooling assessment.
- [ExLlamaV3](https://github.com/turboderp-org/exllamav3) — turboderp-org (accessed 2026-10-11): EXL3 quantization + inference library for consumer GPUs with MoE CPU offload, speculative decoding and TabbyAPI backend; the natural fit for a 12GB RTX 4070 Ti (axis 1b). Performance claims unverified.
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
- [2026-10-11] Daily sweeps absent 10-06..10-14 (only 2026-10-05 ran after the 41-day gap). Vendor/lab blog feeds (all 10 in SOURCES primary list) never logged as opened or degraded. Status: OPEN; 2026-10-15 daily run resumed scanning.
- [2026-10-15] Vendor blog primary feeds (Microsoft, Google, Anthropic, OpenAI, Protect AI, HiddenLayer, Lakera, Trail of Bits, Wiz, Elastic) — searched but no October 2026 posts found via web search; individual blog indexes not opened this run (prioritized CVE/paper/advisory lanes). Non-blocking but coverage gap persists.
