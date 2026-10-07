# AI-ML-RedTeam Radar — Trend ledger

Single source of truth. The README and reports are derived from this file.
Last updated: 2026-10-07

Trend stages: `seed` → `emerging` → `accelerating` → `mainstreaming` → `dormant`.
Evidence line format: `date — primary URL — one line of context`. Max 10 per trend.

---

## trends

### id: local-inference-001 — Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)
- stage: accelerating
- confidence: high
- last_evidence: 2026-10-07
- aliases: [Bleeding Llama, Breaking Local AI Runtimes]
- notes: Critical CVE cluster spanning the entire local/self-hosted inference stack (llama.cpp, Ollama, vLLM, LMDeploy, NVIDIA Triton, Xinference); attack classes include GGUF parser overflows, server use-after-free, SSRF via multimodal endpoints, authentication bypass, and assert-based security check bypasses. In-the-wild exploitation confirmed (LMDeploy CVE-2026-33626 weaponized within 12h of disclosure). Promoted emerging→accelerating 2026-10-07: ≥7 independent orgs, in-the-wild exploitation, 9 evidence items spanning the full local inference stack.
- evidence:
  - 2026-08-21 — https://github.com/advisories/GHSA-x2rj-828p-hx9m — Xinference CVE-2026-61539: unsafe eval() on Llama3 tool-call parser output → unauth RCE, CVSS 10.0, fixed v2.7.0.
  - 2026-08-24 — https://github.com/advisories/GHSA-x8qc-fggm-mpqg — Ollama CVE-2026-7482 "Bleeding Llama": crafted GGUF → heap OOB read → memory (env vars, API keys, system prompts) exfiltrated via /api/push. Floor 0.17.1.
  - 2026-08-24 — https://github.com/advisories/GHSA-3p4r-fq3f-q74v — llama.cpp CVE-2026-27940: GGUF heap overflow, bypass of the CVE-2025-53630 fix, public RCE PoC. Floor b8146.
  - 2026-08-07 — https://github.com/advisories/GHSA-6hc7-9rph-cm99 — llama.cpp CVE-2026-43631: UAF in llama-server sleep-idle vocab pointer, CVSS 9.2, unauth RCE; builds b7492–b9060.
  - (undated, accessed 2026-10-05) — https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models — Cyera discloses 10 llama.cpp vulnerabilities (2 UAFs CVSS 9.2, integer overflows, OOB); 5 unpatched as of Jun 2026.
  - 2026-04-22 — https://www.sysdig.com/blog/cve-2026-33626-how-attackers-exploited-lmdeploy-llm-inference-engines-in-12-hours — LMDeploy CVE-2026-33626 SSRF exploited in-the-wild within 12h31m of advisory; attacker port-scanned IMDS/internal services.
  - (undated, accessed 2026-10-05) — https://www.stingrai.io/blog/inference-server-security-vllm-triton-ollama-2026 — Roundup: NVIDIA Triton CVE-2026-24207 auth bypass CVSS 9.8 (fixed 26.03), vLLM CVE-2026-22778 RCE CVSS 9.8 (fixed 0.14.1), llama.cpp CVE-2026-33298.
  - 2026-05-05 — https://www.cyera.com/research/bleeding-llama-critical-unauthenticated-memory-leak-in-ollama — Cyera: ~300k exposed Ollama servers; CVE-2026-7482 exfiltrates API keys/prompts via crafted GGUF + /api/push; no methodology for server count disclosed.
  - 2026-06-14 — https://github.com/advisories/GHSA-q8gq-377p-jq3r — vLLM CVE-2026-41523: assert-based security check in activation-function loading bypassed in Python optimized mode → arbitrary code execution via malicious HuggingFace model; CVSS 7.5, fixed 0.22.0.

### id: agentic-injection-001 — Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)
- stage: accelerating
- confidence: high
- last_evidence: 2026-10-06
- aliases: [tool poisoning, skill injection, skill poisoning, memory injection, indirect prompt injection, IPI, hook poisoning, HookPry, SkillPoison]
- notes: Attack surface spans agent subsystems — MCP tool descriptions, coding-agent skills, persistent agent memory, lifecycle hooks, coding-agent harness security — plus a growing impossibility-result literature and defensive frameworks. Promoted emerging→accelerating 2026-10-07: 10/10 evidence slots filled from ≥10 independent research groups; attack success rates consistently >90%; defenses lag (best PI detector catches 2% of AgentDojo injections at 1% FPR; auto-approval settings raise attack success from 29.2% to 95.6%).
- evidence:
  - 2026-03-23 — https://arxiv.org/abs/2603.22489 — STRIDE/DREAD threat model of the MCP stack; tool poisoning is the top client-side vulnerability; 5/7 major MCP clients lack static validation of tool descriptions.
  - 2026-08-22 — https://arxiv.org/abs/2608.21929 — SkillBloat: malicious coding-agent "skills" as a trusted instruction channel; token-amplification (resource-abuse) attacks reaching 5.4–10.1x average best amplification.
  - 2026-08-23 — https://arxiv.org/abs/2608.22248 — AEGIS: instruction/data separation via latent instruction manifolds; multi-layer consensus detector for indirect prompt injection with lower over-refusal.
  - 2026-08-24 — https://arxiv.org/abs/2608.23471 — InjecMEM: single-interaction memory injection steers later retrieval-conditioned responses of LLM agents; retriever-agnostic anchor + adversarial command, transfers across backbones.
  - 2026-08-24 — https://arxiv.org/abs/2608.22868 — AgentFlow: flow-centric policy language + runtime reference monitor; on 949 AgentDojo injected cases cuts confirmed compromise 33.0%→0.0% while raising utility.
  - 2026-05-17 — https://arxiv.org/abs/2605.17634 — "AI Agents May Always Fall for Prompt Injections": impossibility result via Contextual Integrity theory; adversary can always construct a context making a blocked flow appear legitimate.
  - 2026-09-03 — https://arxiv.org/abs/2609.03884 — HookPry: attacker-controlled lifecycle-hook updates steer AI agent harnesses; 92.5% per-harness success rate across 7 harnesses; Microsoft Defender 0% detection.
  - 2026-10-02 — https://arxiv.org/abs/2610.03448 — PI detector re-evaluation: best detector on BIPIA catches only 2% of AgentDojo injections at 1% FPR; benchmark scores mislead deployment decisions.
  - 2026-10-06 — https://arxiv.org/abs/2610.07645 — SkillPoison: progressive skill poisoning via verified successful experiences; 95.71% attack success rate while all injected experiences remain task-correct; bypasses verification and lexical inspection.
  - 2026-10-06 — https://arxiv.org/abs/2610.07639 — HarnessSecurity-Bench: first systematic benchmark of coding-agent harness security across 6 harnesses (incl. Claude Code, Codex CLI); auto-approval raises attack success 29.2%→95.6%; 2,500 trials, 81,155 tool calls.

### id: ai-supplychain-001 — AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)
- stage: seed
- confidence: high
- last_evidence: 2026-10-07
- aliases: [nullifAI, FaceHugger, model poisoning, conjunctive poisoning, pickle deserialization, trust_remote_code bypass]
- notes: Attack surface spans model-hub poisoning (pickle/safetensors, malicious repos), library-level code execution bypasses (HF diffusers TOCTOU), deployment-artifact tampering (prompt wrappers + config metadata), instruction backdoors in customized coding LLMs, and assert-based security check bypasses in inference servers loading untrusted models. Hugging Face breach (Jul 2026) demonstrated autonomous-agent exploitation of the model-hub attack surface at scale. ≥5 independent sources + concrete artifacts.
- evidence:
  - 2026-07-20 — https://www.helpnetsecurity.com/2026/07/20/hugging-face-breached-by-autonomous-ai-agent/ — Hugging Face breach: autonomous AI agent exploited dataset-loader + template-injection vulns → node-level access, cloud/cluster credential harvest, lateral movement across clusters.
  - 2026-07-27 — https://www.zafran.io/resources/facehugger-vulnerabilities-in-hugging-face-diffusers-open-door-to-supply-chain-attacks-on-enterprise-ai — FaceHugger: CVE-2026-44827/45804/44513 (CVSS 8.8/7.5) in HF diffusers; TOCTOU bypasses trust_remote_code → silent arbitrary code execution; fixed diffusers 0.38.0.
  - 2026-08-16 — https://arxiv.org/abs/2608.15913 — Conjunctive Poisoning: malicious deployment artifacts (prompt wrappers + metadata) deterministically alter model behavior without weight modification; existing defenses (PromptShield, SigStore) insufficient.
  - 2026-08-06 — https://arxiv.org/abs/2608.05659 — ARIA: automated instruction backdoor attacks on customized coding LLMs; 0.945 attack success rate, 1.000 false negative rate against detection mechanisms.
  - 2026-06-14 — https://github.com/advisories/GHSA-q8gq-377p-jq3r — vLLM CVE-2026-41523: malicious HuggingFace model exploits assert-based activation-function validation → arbitrary code execution when vLLM runs in Python optimized mode; CVSS 7.5, fixed 0.22.0.

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
- [resolved 2026-10-07] vLLM CVE-2026-41523 — verified via GHSA-q8gq-377p-jq3r (opened); routed as evidence to local-inference-001 and ai-supplychain-001.
- [resolved 2026-10-07] PyRIT archived — CORRECTED: github.com/Azure/PyRIT is an archived stub; active development continues at github.com/microsoft/PyRIT (v1.1.0, Sep 4 2026, 37+ contributors).
- [resolved 2026-10-07] ExLlamaV2 archived → ExLlamaV3 — VERIFIED: ExLlamaV3 at github.com/turboderp-org/exllamav3, v1.5.4 (Oct 3), 1.6K stars, EXL3 quantization. Moved to study_shelf.
- [resolved 2026-10-07] Ollama v0.40.0-rc3 MLX runtime — VERIFIED: v0.40.0 released Sep 25 (MLX default on Apple Silicon, decision models).
- [resolved 2026-10-07] Unsloth MoE fine-tuning — VERIFIED via Unsloth blog (Feb 10 2026): 12x MoE speedup, gpt-oss-20b on 12.8GB VRAM. Moved to study_shelf.
- [resolved 2026-10-07] OWASP GenAI LLM Top 10 2026 — VERIFIED via genai.owasp.org primary (published Aug 3 2026): incident-weighted methodology (75% vote / 25% data from 6,639 incidents); Excessive Agency → LLM03, Hidden Context Exposure replaces System Prompt Leakage. Moved to study_shelf.
- [queued 2026-08-25] Hydra config-instantiation RCE — CVE-2026-68508 / GHSA-2cp2-2r3c-7p7r verified via GitHub Advisory Database (published 2026-08-21): `hydra.utils.instantiate` with untrusted config → code execution; widely used for ML experiment configs — missing: ≥2 more independent sources on ML-pipeline config-RCE to seed a trend.
- [queued 2026-08-24] ACM WPLL 2026 paper: inference-time jailbreak defenses consistently bypassed by long reasoning-heavy prompts (open-source models incl. Llama 3.2, Mistral, Qwen, Gemma) — missing: open the paper page.
- [queued 2026-10-07] Promptfoo acquired by OpenAI (Mar 9 2026) — major red-team tooling landscape shift; 25%+ Fortune 500 adoption; open-source maintenance committed — missing: open primary announcement (siliconangle.com or OpenAI blog).
- [queued 2026-10-07] PEV jailbreak (arXiv 2610.07125, Oct 5) — random embedding perturbations jailbreak all tested open-weight LLMs; 100% success on JailbreakBench within 1 minute — missing: ≥2 more independent embedding-attack papers to seed a trend.
- [queued 2026-10-07] Answer-side backdoor (arXiv 2610.07723, Oct 6) — model self-generates trigger in first turn, activating backdoor in subsequent turns; ~100% ASR at 5% poisoning rate — relates to ai-supplychain-001 if cluster grows.
- [queued 2026-10-07] MCP server exposure at scale — reports claim 5,832/9,695 servers vulnerable, 70% return tool catalog to anonymous callers — missing: open a primary source (research report or advisory, not news aggregators).
- [queued 2026-10-07] RAG-PIBench (arXiv 2610.08571, Oct 6) — leakage-aware prompt-injection detection benchmark for RAG; best detector (DistilBERT) F1 0.896 — relates to agentic-injection-001 defensive landscape.
- [queued 2026-10-07] CVE-2026-34159 llama.cpp RPC backend — deserialize_tensor() skips bounds validation when buffer=0 → arbitrary memory R/W, CVSS 9.8, fixed b8492 — missing: open NVD or GHSA primary directly.

## study_shelf

<!--
0–2 picks per daily run, newest first. Format:
- [Title](primary URL) — source (YYYY-MM-DD): one line on why it matters.
Prune picks older than 30 days on weekly runs.
-->

- [ExLlamaV3 v1.5.4](https://github.com/turboderp-org/exllamav3/releases) — turboderp-org (2026-10-03): consumer-GPU inference library with EXL3 quantization (based on QTIP), speculative decoding, CPU MoE offload; 1.6K stars, 48 releases. Directly relevant to the 1b stack for RTX 4070 Ti builds.
- [OWASP GenAI LLM Top 10 2026](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/) — OWASP (2026-08-03): first incident-weighted LLM risk taxonomy (6,639 real incidents); Excessive Agency climbs to LLM03, Hidden Context Exposure replaces System Prompt Leakage. Baseline for red-team scoping.
- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): lifecycle hooks in agent harnesses are a blindspot — 92.5% compromise rate across 7 harnesses, 0% detection. Directly relevant when assessing local agent setups with plugin/hook systems.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): systematic audit of the most widely-used local inference engine; 5 of 10 bugs unpatched — essential reading for anyone running llama.cpp in production or red-teaming local deployments.
- [Unsloth 2026 MoE Update](https://unslothai.substack.com/p/unsloth-2026-update-faster-moe) — Unsloth (2026-02-10): 12x faster MoE fine-tuning with 35%+ less VRAM; gpt-oss-20b fits 12.8GB VRAM; supports Qwen3/DeepSeek/GLM families. Directly relevant to scope 1b for RTX 4070 Ti QLoRA workflows.
- [InjecMEM: Memory Injection Attack on LLM Agent Memory Systems](https://arxiv.org/abs/2608.23471) — arXiv (2026-08-24): agent memory is now a demonstrated injection target — one interaction poisons later retrieval-conditioned answers; directly relevant when red-teaming local agents with memory/RAG stacks.
- [llama.cpp v0.3.0](https://github.com/ggml-org/llama.cpp/releases/tag/v0.3.0) — ggml-org (2026-08-25): first v0.3.x tag — dots3-note multimodal (new DSA-ISWA KV cache), MTP for GLM-4.5-Air, DeepSeek 4 tensor-split fixes, ggml v0.22.0.

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
