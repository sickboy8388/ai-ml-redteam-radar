# AI-ML-RedTeam Radar — Trend ledger

Single source of truth. The README and reports are derived from this file.
Last updated: 2026-08-24 (first daily run)

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

(none yet — seeded by the first daily run)

## observation_queue

<!--
Unverified or sub-bar items. Format:
- [queued YYYY-MM-DD] <what> — <why interesting> — <what is missing to promote>
Hard cap ~25 live items.
-->

- [queued 2026-08-24] MCP tool poisoning / agentic prompt-injection cluster — arXiv 2603.22489 verified (1 source, below trend bar); corroborating leads not yet opened: Microsoft "State of MCP Security 2026" (techcommunity.microsoft.com), OWASP MCP Tool Poisoning page, Aptible writeup citing an April 2026 Johns Hopkins PR-title injection hijack of Claude Code/Gemini CLI/Copilot — missing: open ≥2 more primaries to promote to seed.
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

(none yet)

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

(none)
