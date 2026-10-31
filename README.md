# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-3-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--31-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-31)

- **NEW TREND agentic-offense-001 seeded**: AI agents in real-world offensive operations — Wiz documents 6+ attack campaigns with 7 behavioral fingerprints (ARTEX/Storm-0940, Hermes, Flowise mass-exploitation, MCP-backend exfiltration); Sysdig captured the first in-wild LLM-agent post-exploitation (CVE-2026-39987, DB exfil in <1h). ≥7 independent orgs.
- **llm-frontend-001 PROMOTED seed→emerging**: IBM published 25 Langflow OSS GHSAs on Oct 29 (6 Critical CVSS 9.8 RCEs, 8 High); the app-layer attack surface is deeper and more severe than expected.
- **local-inference-001** (accelerating, held): vLLM disclosed 8 new GHSAs Oct 28 including High pickle deserialization via forged SHM handles (Trail of Bits, found using GPT-5.5-Cyber) and Ghostscript RCE; all fixed in 0.32.0. llama.cpp up to b12019; Ollama v0.40.13.
- **agentic-injection-001** (accelerating, held): 5+ new independent papers Oct 28-30 — CARI cross-boundary injection 94.8% ASR, SEAL defense drops ASR to 0.1%, self-evolution degrades IPI robustness.
- **Queue**: resolved 5, promoted 1 → 3 live items. GhostAction resurgence confirmed via StepSecurity primary (345 repos, credential exfil from full git history).

## Trends

seed 1 · emerging 2 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-28](https://github.com/advisories/GHSA-6757-hggm-hp2w) — vLLM CVE-2026-115912: forged SHM handles reach pickle.loads() in worker (High, fixed 0.32.0) |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-28](https://arxiv.org/abs/2610.38799) — CARI: cross-boundary runtime injection in coding-agent workflows, 94.8% ASR |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-26](https://arxiv.org/abs/2610.35043) — Steering-plugin trojans: 97.8% ASR hijacking via trojanized LLM activation-steering plugins |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-10-29](https://github.com/advisories/GHSA-vfwm-g9g9-v2g5) — IBM Langflow OSS 25-advisory batch: 6 Critical RCEs (CVSS 9.8), 8 High |
| [AI agents in real-world offensive operations (ARTEX, agentic intrusion chains)](TRENDS.md#trends) | seed | [2026-10-29](https://www.wiz.io/blog/the-rise-of-agentic-attacks) — Wiz: 6+ real-world AI-agent-driven attack campaigns, 7 behavioral fingerprints |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12019 (2026-10-31); cpp-httplib 0.64.0, KV-cache rotation GPU buffers; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.13 (2026-10-28, LFM3 cross-platform Linux/Windows); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18); 8 new GHSAs Oct 28 (pickle deser High, Ghostscript RCE High); security floor: ≥0.32.0
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.1 (2026-10-30); v5.22.0 adds Mistral Large 4 (1T/52B-active MoE, 1M context), FP8 backward for LoRA
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — 1.6.5 (2026-10-25): EXL3 quantization, CPU MoE offload, speculative decoding; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.913-beta (2026-10-30): multi-LoRA batching, DeepSeek-V4.1-Flash GGUFs, 2x faster Qwen-Image rendering under 16GB VRAM

## Worth studying

- [CARI: Cross-Boundary Adversarial Runtime Injection in Coding-Agent Workflows](https://arxiv.org/abs/2610.38799) — arXiv (2026-10-28): malicious peer component injects instructions via runtime diagnostic output; 94.8% ASR, 61.3% on Codex, 58.7% on Claude Code. Critical for multi-component coding agents.
- [SEAL: Sealed Queries for Local Sanitization against Indirect Prompt Injection](https://arxiv.org/abs/2610.39758) — arXiv (2026-10-29): defense drops AgentDojo PI ASR from 34.6% to 0.1% with 127x fewer defense tokens. First practical low-overhead PI defense.
- [Wiz: The Rise of Agentic Attacks](https://www.wiz.io/blog/the-rise-of-agentic-attacks) — Wiz (2026-10-29): 6+ real-world AI-agent-driven attack campaigns with 7 behavioral fingerprints; essential reading for anyone defending against or emulating agentic threats.
- [Sysdig: AI Agent at the Wheel](https://www.sysdig.com/blog/ai-agent-at-the-wheel-how-an-attacker-used-llms-to-move-from-a-cve-to-an-internal-database-in-4-pivots) — Sysdig (2026-05-26): first documented in-wild LLM-agent post-exploitation; CVE-2026-39987 to DB exfil in <1h.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): systematic audit of llama.cpp; 5 of 10 bugs unpatched.

## How it works

A scheduled routine runs a fixed prompt: *read `AGENTS.md`, then `routines/daily.md`, and
execute it.* The agent sweeps the sources in [`SOURCES.md`](SOURCES.md), routes new
published artifacts into the [trend ledger](TRENDS.md), writes a dated report under
[`reports/`](reports/), regenerates this page, and commits. A weekly routine recalibrates
trends and prunes.

This is a **radar**: it points to published research, tools, and advisories and summarizes
their significance. It tracks artifacts — it is not a runbook and stores no operational
payloads or jailbreak strings.

---
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-31.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
