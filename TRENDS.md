# AI-ML-RedTeam Radar — Trend ledger

Single source of truth. The README and reports are derived from this file.
Last updated: 2026-08-25 (second daily run)

Trend stages: `seed` → `emerging` → `accelerating` → `mainstreaming` → `dormant`.
Evidence line format: `date — primary URL — one line of context`. Max 10 per trend.

---

## trends

<!--
Seed the ledger by running the daily routine. Each trend block looks like:

### id: local-inference-001 — <short name>
- stage: seed
- confidence: low|medium|high
- last_evidence: YYYY-MM-DD
- aliases: [...]
- notes: scope note
- evidence:
  - YYYY-MM-DD — https://... — one line of context
-->

### id: local-inference-001 — Self-hosted inference server attack surface (GGUF parsing & unauth model-management APIs)
- stage: seed
- confidence: medium
- last_evidence: 2026-08-21
- aliases: [Bleeding Llama]
- notes: CVE cluster across the local/self-hosted serving stack (Ollama, llama.cpp, Xinference); model output and model files as attacker-controlled input to the server.
- evidence:
  - 2026-08-21 — https://github.com/advisories/GHSA-x2rj-828p-hx9m — Xinference CVE-2026-61539: unsafe eval() on Llama3 tool-call parser output → unauth RCE, CVSS 10.0, fixed v2.7.0.
  - 2026-08-24 — https://github.com/advisories/GHSA-x8qc-fggm-mpqg — Ollama CVE-2026-7482 "Bleeding Llama": crafted GGUF → heap OOB read → memory (env vars, API keys, system prompts) exfiltrated via /api/push. Floor 0.17.1.
  - 2026-08-24 — https://github.com/advisories/GHSA-3p4r-fq3f-q74v — llama.cpp CVE-2026-27940: GGUF heap overflow, bypass of the CVE-2025-53630 fix, public RCE PoC. Floor b8146.

### id: agentic-injection-001 — Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory)
- stage: seed
- confidence: medium
- last_evidence: 2026-08-24
- aliases: [tool poisoning, skill injection, memory injection, indirect prompt injection, IPI]
- notes: attack surface is shifting from single-prompt injection to agent subsystems — MCP tool descriptions, coding-agent "skills", persistent agent memory — plus a growing defensive literature (flow policies, latent-manifold detectors). Promoted from observation_queue on 2026-08-25 (≥3 independent groups + concrete artifacts).
- evidence:
  - 2026-03-23 — https://arxiv.org/abs/2603.22489 — STRIDE/DREAD threat model of the MCP stack; tool poisoning is the top client-side vulnerability; 5/7 major MCP clients lack static validation of tool descriptions.
  - 2026-08-22 — https://arxiv.org/abs/2608.21929 — SkillBloat: malicious coding-agent "skills" as a trusted instruction channel; token-amplification (resource-abuse) attacks reaching 5.4–10.1x average best amplification.
  - 2026-08-23 — https://arxiv.org/abs/2608.22248 — AEGIS: instruction/data separation via latent instruction manifolds; multi-layer consensus detector for indirect prompt injection with lower over-refusal.
  - 2026-08-24 — https://arxiv.org/abs/2608.23471 — InjecMEM: single-interaction memory injection steers later retrieval-conditioned responses of LLM agents; retriever-agnostic anchor + adversarial command, transfers across backbones.
  - 2026-08-24 — https://arxiv.org/abs/2608.22868 — AgentFlow: flow-centric policy language + runtime reference monitor; on 949 AgentDojo injected cases cuts confirmed compromise 33.0%→0.0% while raising utility.

## observation_queue

<!--
Unverified or sub-bar items. Format:
- [queued YYYY-MM-DD] <what> — <why interesting> — <what is missing to promote>
Hard cap ~25 live items.
-->

- [promoted 2026-08-25] MCP tool poisoning / agentic prompt-injection cluster → trend `agentic-injection-001`: cleared the bar with 4 new independent primaries this run (InjecMEM, SkillBloat, AgentFlow, AEGIS). Vendor leads (Microsoft "State of MCP Security 2026", Aptible/Johns Hopkins PR-title hijack writeup) remain unopened — re-queue as corroboration targets:
- [queued 2026-08-25] Vendor MCP-security writeups — Microsoft "State of MCP Security 2026" (techcommunity.microsoft.com) + Aptible writeup on the April 2026 PR-title injection hijack of Claude Code/Gemini CLI/Copilot — missing: open both primaries; would raise `agentic-injection-001` confidence.
- [queued 2026-08-25] Hydra config-instantiation RCE — CVE-2026-68508 / GHSA-2cp2-2r3c-7p7r verified via GitHub Advisory Database (published 2026-08-21): `hydra.utils.instantiate` with untrusted config → code execution; widely used for ML experiment configs — missing: ≥2 more independent sources on ML-pipeline config-RCE to seed a trend.
- [queued 2026-08-25] OWASP GenAI LLM Top 10 2026 — published 2026-08-04, project page verified (owasp.org, accessed 2026-08-25); canonical source now the GenAI-Security-Project repo — missing: diff vs 1.1 list and open the 2026 final document before routing as taxonomies-axis evidence.
- [queued 2026-08-24] Malicious models on Hugging Face as malware distribution — lead: hivesecurity.gitlab.io writeup on fake `Open-OSS/privacy-filter` repo (#1 trending, 244k downloads in 18h, May 2026) + CVE-2026-6859 (InstructLab hardcoded trust_remote_code=True) — missing: open the writeup and the CVE advisory to verify.
- [queued 2026-08-24] Cyera "Bleeding Llama" research blog (cyera.com) claims ~300k exposed Ollama servers — advisory verified via GHSA, exposure count unverified — missing: open Cyera post.
- [queued 2026-08-24] ACM WPLL 2026 paper: inference-time jailbreak defenses consistently bypassed by long reasoning-heavy prompts (open-source models incl. Llama 3.2, Mistral, Qwen, Gemma) — missing: open the paper page.
- [queued 2026-08-24] NVIDIA Triton Inference Server auth bypass CVE-2026-24207/-24209/-24210/-24215 (fixed 26.03) — surfaced via secondary briefing — missing: open NVIDIA PSIRT/NVD records; likely belongs to local-inference-001.

## study_shelf

<!--
0–2 picks per daily run, newest first. Format:
- [Title](primary URL) — source (YYYY-MM-DD): one line on why it matters.
Prune picks older than 30 days on weekly runs.
-->

- [InjecMEM: Memory Injection Attack on LLM Agent Memory Systems](https://arxiv.org/abs/2608.23471) — arXiv (2026-08-24): agent memory is now a demonstrated injection target — one interaction poisons later retrieval-conditioned answers; directly relevant when red-teaming local agents with memory/RAG stacks.
- [llama.cpp v0.3.0](https://github.com/ggml-org/llama.cpp/releases/tag/v0.3.0) — ggml-org (2026-08-25): first v0.3.x tag — dots3-note multimodal (new DSA-ISWA KV cache), MTP for GLM-4.5-Air, DeepSeek 4 tensor-split fixes, ggml v0.22.0; the local-runtime baseline moved.

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

## blockers

<!--
Access/tooling blockers that prevented verification. Format:
- [YYYY-MM-DD] <what is blocked> — <what was tried> — <status>
-->

- [2026-08-25] State persistence across scheduled sessions — session sandbox started empty (repo absent at /mnt/agents/output); recovered by cloning the GitHub remote during a curator-granted public window. Future scheduled runs CANNOT re-clone once the repo is private again (no credentials persist across sessions) — status: OPEN, curator must either keep the repo clone present in the persistent mount, provide a credential that survives sessions, or accept that each run restores from GitHub manually. Escalated per Hard rules → Operator notifications.
- [2026-08-25] r/LocalLLaMA (reddit.com) — JSON endpoint rejected again, 2nd consecutive run — degraded; community-pulse lane uncovered.
