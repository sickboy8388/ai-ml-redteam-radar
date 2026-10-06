# AI-ML-RedTeam Radar — Trend ledger

Single source of truth. The README and reports are derived from this file.
Last updated: 2026-10-06

Trend stages: `seed` → `emerging` → `accelerating` → `mainstreaming` → `dormant`.
Evidence line format: `date — primary URL — one line of context`. Max 10 per trend.

---

## trends

### id: local-inference-001 — Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)
- stage: emerging
- confidence: high
- last_evidence: 2026-10-05
- aliases: [Bleeding Llama, Breaking Local AI Runtimes]
- notes: Critical CVE cluster spanning the entire local/self-hosted inference stack (llama.cpp, Ollama, vLLM, LMDeploy, NVIDIA Triton, Xinference); attack classes include GGUF parser overflows, server use-after-free, SSRF via multimodal endpoints, and authentication bypass. In-the-wild exploitation confirmed (LMDeploy CVE-2026-33626 weaponized within 12h of disclosure). Promoted seed→emerging 2026-10-05: ≥6 independent orgs (Cyera, Sysdig, NVIDIA, Orca Security, GHSA maintainers, StingRAI) + concrete artifacts across the stack.
- evidence:
  - 2026-08-21 — https://github.com/advisories/GHSA-x2rj-828p-hx9m — Xinference CVE-2026-61539: unsafe eval() on Llama3 tool-call parser output → unauth RCE, CVSS 10.0, fixed v2.7.0.
  - 2026-08-24 — https://github.com/advisories/GHSA-x8qc-fggm-mpqg — Ollama CVE-2026-7482 "Bleeding Llama": crafted GGUF → heap OOB read → memory (env vars, API keys, system prompts) exfiltrated via /api/push. Floor 0.17.1.
  - 2026-08-24 — https://github.com/advisories/GHSA-3p4r-fq3f-q74v — llama.cpp CVE-2026-27940: GGUF heap overflow, bypass of the CVE-2025-53630 fix, public RCE PoC. Floor b8146.
  - 2026-08-07 — https://github.com/advisories/GHSA-6hc7-9rph-cm99 — llama.cpp CVE-2026-43631: UAF in llama-server sleep-idle vocab pointer, CVSS 9.2, unauth RCE; builds b7492–b9060.
  - (undated, accessed 2026-10-05) — https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models — Cyera discloses 10 llama.cpp vulnerabilities (2 UAFs CVSS 9.2, integer overflows, OOB); 5 unpatched as of Jun 2026.
  - 2026-04-22 — https://www.sysdig.com/blog/cve-2026-33626-how-attackers-exploited-lmdeploy-llm-inference-engines-in-12-hours — LMDeploy CVE-2026-33626 SSRF exploited in-the-wild within 12h31m of advisory; attacker port-scanned IMDS/internal services.
  - (undated, accessed 2026-10-05) — https://www.stingrai.io/blog/inference-server-security-vllm-triton-ollama-2026 — Roundup: NVIDIA Triton CVE-2026-24207 auth bypass CVSS 9.8 (fixed 26.03), vLLM CVE-2026-22778 RCE CVSS 9.8 (fixed 0.14.1), llama.cpp CVE-2026-33298.
  - 2026-05-05 — https://www.cyera.com/research/bleeding-llama-critical-unauthenticated-memory-leak-in-ollama — Cyera: ~300k exposed Ollama servers; CVE-2026-7482 exfiltrates API keys/prompts via crafted GGUF + /api/push; no methodology for server count disclosed.

### id: agentic-injection-001 — Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)
- stage: emerging
- confidence: high
- last_evidence: 2026-10-05
- aliases: [tool poisoning, skill injection, memory injection, indirect prompt injection, IPI, hook poisoning, HookPry, runaway reaction, skill composition]
- notes: Attack surface spans agent subsystems — MCP tool descriptions, coding-agent skills, persistent agent memory, lifecycle hooks — plus a growing impossibility-result literature and defensive frameworks. Promoted seed→emerging 2026-10-05: ≥8 independent research groups + in-the-wild MCP tool-poisoning rates exceeding 60% reported. 2026-10-06: skill-composition attacks (CRIME) and internet-facing MCP server assessment (91% lack OAuth) added; now 10/10 evidence slots filled.
- evidence:
  - 2026-03-23 — https://arxiv.org/abs/2603.22489 — STRIDE/DREAD threat model of the MCP stack; tool poisoning is the top client-side vulnerability; 5/7 major MCP clients lack static validation of tool descriptions.
  - 2026-08-22 — https://arxiv.org/abs/2608.21929 — SkillBloat: malicious coding-agent "skills" as a trusted instruction channel; token-amplification (resource-abuse) attacks reaching 5.4–10.1x average best amplification.
  - 2026-08-23 — https://arxiv.org/abs/2608.22248 — AEGIS: instruction/data separation via latent instruction manifolds; multi-layer consensus detector for indirect prompt injection with lower over-refusal.
  - 2026-08-24 — https://arxiv.org/abs/2608.23471 — InjecMEM: single-interaction memory injection steers later retrieval-conditioned responses of LLM agents; retriever-agnostic anchor + adversarial command, transfers across backbones.
  - 2026-08-24 — https://arxiv.org/abs/2608.22868 — AgentFlow: flow-centric policy language + runtime reference monitor; on 949 AgentDojo injected cases cuts confirmed compromise 33.0%→0.0% while raising utility.
  - 2026-05-17 — https://arxiv.org/abs/2605.17634 — "AI Agents May Always Fall for Prompt Injections": impossibility result via Contextual Integrity theory; adversary can always construct a context making a blocked flow appear legitimate.
  - 2026-09-03 — https://arxiv.org/abs/2609.03884 — HookPry: attacker-controlled lifecycle-hook updates steer AI agent harnesses; 92.5% per-harness success rate across 7 harnesses; Microsoft Defender 0% detection.
  - 2026-10-02 — https://arxiv.org/abs/2610.03448 — PI detector re-evaluation: best detector on BIPIA catches only 2% of AgentDojo injections at 1% FPR; benchmark scores mislead deployment decisions.
  - 2026-10-05 — https://arxiv.org/abs/2610.05943 — Runaway Reaction (CRIME framework): individually vetted benign agent skills compose into malicious behaviors; evaluated 4,000 public skills across 8 cybersecurity attack behaviors.
  - 2026-07-31 — https://arxiv.org/abs/2608.00150 — Exposed by Design: dynamic assessment of 414 internet-facing MCP servers; 91% lack OAuth, 687 shell-exec tool instances, 68 reportable vulns (SQLi, SSRF, path traversal); Corvus tool released.

### id: ai-supplychain-001 — AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)
- stage: emerging
- confidence: high
- last_evidence: 2026-08-16
- aliases: [nullifAI, FaceHugger, model poisoning, conjunctive poisoning, pickle deserialization, trust_remote_code bypass, assert bypass]
- notes: Seeded 2026-10-05. Promoted seed→emerging 2026-10-06: 5 independent sources (HelpNetSecurity, Zafran, arXiv×2, huntr/vLLM) + concrete artifacts (CVEs, breach report, papers). Attack surface spans model-hub poisoning (pickle/safetensors, malicious repos), library-level code execution bypasses (HF diffusers TOCTOU, vLLM assert-based check bypass), deployment-artifact tampering (prompt wrappers + config metadata), and instruction backdoors in customized coding LLMs. Hugging Face breach (Jul 2026) demonstrated autonomous-agent exploitation of the model-hub attack surface at scale.
- evidence:
  - 2026-07-20 — https://www.helpnetsecurity.com/2026/07/20/hugging-face-breached-by-autonomous-ai-agent/ — Hugging Face breach: autonomous AI agent exploited dataset-loader + template-injection vulns → node-level access, cloud/cluster credential harvest, lateral movement across clusters.
  - 2026-07-27 — https://www.zafran.io/resources/facehugger-vulnerabilities-in-hugging-face-diffusers-open-door-to-supply-chain-attacks-on-enterprise-ai — FaceHugger: CVE-2026-44827/45804/44513 (CVSS 8.8/7.5) in HF diffusers; TOCTOU bypasses trust_remote_code → silent arbitrary code execution; fixed diffusers 0.38.0.
  - 2026-08-16 — https://arxiv.org/abs/2608.15913 — Conjunctive Poisoning: malicious deployment artifacts (prompt wrappers + metadata) deterministically alter model behavior without weight modification; existing defenses (PromptShield, SigStore) insufficient.
  - 2026-08-06 — https://arxiv.org/abs/2608.05659 — ARIA: automated instruction backdoor attacks on customized coding LLMs; 0.945 attack success rate, 1.000 false negative rate against detection mechanisms.
  - 2026-06-14 — https://github.com/advisories/GHSA-q8gq-377p-jq3r — vLLM CVE-2026-41523: assert-based security check bypass in activation-function loading allows arbitrary code execution via malicious HuggingFace model when Python runs in optimized mode; CVSS 7.5; fixed 0.22.0.

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
- [queued 2026-08-25] Hydra config-instantiation RCE — CVE-2026-68508 / GHSA-2cp2-2r3c-7p7r verified via GitHub Advisory Database (published 2026-08-21): `hydra.utils.instantiate` with untrusted config → code execution; widely used for ML experiment configs — missing: ≥2 more independent sources on ML-pipeline config-RCE to seed a trend.
- [queued 2026-08-25] OWASP GenAI LLM Top 10 2026 — published 2026-08-04, confirmed via multiple secondary sources (Imperva, cybersecuritynews); 8/10 categories repositioned, Excessive Agency → LLM03, System Prompt Leakage renamed Hidden Context Exposure — missing: open the canonical OWASP document page before routing as taxonomies-axis evidence.
- [resolved 2026-10-06] vLLM CVE-2026-41523 → opened GHSA-q8gq-377p-jq3r; absorbed into ai-supplychain-001 evidence (assert bypass → RCE via malicious HF model).
- [queued 2026-10-05] PyRIT archived — Microsoft Azure/PyRIT repository archived 2026-03-27, read-only, no releases. Major red-team tooling gap — missing: verify whether development continues elsewhere or is discontinued.
- [resolved 2026-10-06] ExLlamaV2 archived → ExLlamaV3 verified: turboderp-org/exllamav3, v1.5.3 (Sep 27 2026), EXL3 quantization (2–8 bit), tensor/expert-parallel, CPU offload, 50+ model architectures. Added to study_shelf.
- [queued 2026-10-05] Ollama v0.40.0-rc3 MLX runtime — Apple Silicon native support via MLX backend (Sep 25 pre-release) — missing: open release notes and verify scope.
- [queued 2026-10-05, updated 2026-10-06] Unsloth MoE fine-tuning — VERIFIED via primary: 12x MoE speedup, >35% less VRAM; gpt-oss-20b fine-tunes in 12.8GB VRAM (fits RTX 4070 Ti); QLoRA NOT recommended for MoE (use bf16 LoRA); joined PyTorch ecosystem May 2026 — relevant to scope 1b. Not promotable to trend (single tool, not a trend pattern).
- [queued 2026-08-24] ACM WPLL 2026 paper: inference-time jailbreak defenses consistently bypassed by long reasoning-heavy prompts (open-source models incl. Llama 3.2, Mistral, Qwen, Gemma) — missing: open the paper page.
- [queued 2026-10-06] SGLang CVE-2026-86793 — SafeUnpickler bypass (incomplete denylist allows builtins.__import__ + getattr chaining) → unauth RCE via pickle deserialization; affects ≤0.5.18, fix incomplete remediation of CVE-2025-10164 — relates to local-inference-001 and ai-supplychain-001; missing: open GHSA-m675-99qc-9233 primary.
- [queued 2026-10-06] LiteLLM 6 CVEs (CVSS 10.0 chain) — CVE-2026-42271 command injection + Starlette host-header bypass → unauth RCE; CVE-2026-42208 pre-auth SQLi CVSS 9.8; CISA KEV; in-the-wild SQLi exploitation 36h post-disclosure; PyPI supply-chain attack (v1.82.7–8 backdoored Mar 2026) — verified via danilchenko.dev primary. Candidate for local-inference-001 or new AI-gateway sub-trend.
- [queued 2026-10-06] GitLab AI Gateway CVE-2026-90970 CVSS 9.9 — authenticated Duo Agent Platform users escape prompt-template sandbox → arbitrary command execution on AI Gateway host — missing: open GitLab advisory primary.
- [queued 2026-10-06] Provider-side indirect prompt injection in proactive agents — arXiv 2610.05266 (Oct 4): external providers embed malicious instructions in their own content; full attack increases target authorization by up to 77.4pp — strengthens agentic-injection-001; opened abstract.
- [queued 2026-10-06] RAISED: self-distillation defense for PI — arXiv 2610.06401 (Oct 5): two-stage self-gen/self-distillation reduces PI attack success rate while preserving utility; defense paper for agentic-injection-001 landscape — opened abstract.
- [queued 2026-10-06] Watermarking causes LLM hallucination — arXiv 2610.04860 (Oct 4, NeurIPS 2026 accepted): all 6 tested watermarking methods consistently produce hallucinations; interventions reduce errors ~90% — new safety/integrity angle; opened abstract.

## study_shelf

<!--
0–2 picks per daily run, newest first. Format:
- [Title](primary URL) — source (YYYY-MM-DD): one line on why it matters.
Prune picks older than 30 days on weekly runs.
-->

- [ExLlamaV3: optimized quantization & inference for consumer GPUs](https://github.com/turboderp-org/exllamav3) — turboderp-org (v1.5.3, 2026-09-27): EXL3 quantization (2–8 bit), tensor/expert-parallel inference, CPU offload for MoE, speculative decoding; 50+ model architectures; TabbyAPI backend provides OpenAI-compatible API. Essential for RTX 4070 Ti operators seeking maximum tokens/s from ≤8B models.
- [Runaway Reaction: When Benign Skills Compose into Malicious Behavior](https://arxiv.org/abs/2610.05943) — arXiv (2026-10-05): CRIME framework shows individually vetted agent skills combine into harmful emergent behaviors; evaluated 4,000 public skills across 8 cybersecurity attack classes. Must-read for anyone building or red-teaming multi-skill agent deployments.
- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): lifecycle hooks in agent harnesses are a blindspot — 92.5% compromise rate across 7 harnesses, 0% detection. Directly relevant when assessing local agent setups with plugin/hook systems.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): systematic audit of the most widely-used local inference engine; 5 of 10 bugs unpatched — essential reading for anyone running llama.cpp in production or red-teaming local deployments.
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
- [2026-10-05] 41-day gap since last scan (2026-08-25 → 2026-10-05) — scheduled runs did not fire or did not persist. Root cause likely the state-persistence blocker above. Status: HEALING — daily runs resumed 2026-10-05, consecutive scan 2026-10-06.
