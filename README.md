# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-6-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--01-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-01, daily)

- **NEW TREND `agentic-offense-001`** (seed): AI agents weaponized for autonomous offensive operations — Wiz documents ARTEX/Storm-0940 hitting 2,250+ M365 tenants, "Black October" (9 AI dev platforms attacked), and a taxonomy of 6+ real-world agentic intrusions from ≥5 independent orgs.
- **`agentic-injection-001`** (accelerating, held): +2 evidence (CARI: 94.8% coding-agent injection ASR; SEAL: defense dropping ASR to 0.1%); paper velocity still extreme.
- **`local-inference-001`** (accelerating, held): no new CVEs; llama.cpp b12030, Ollama v0.40.13, ExLlamaV3 v1.6.6 routine updates.
- **`ai-supplychain-001`** (emerging, held); **`llm-frontend-001`** (seed, held — dormant 2026-11-06 absent new evidence).
- **Queue**: 6 live items; promoted 3 to agentic-offense-001; resolved 2 (Sysdig defense → study_shelf, vLLM batch → confirmed).
- **Study shelf**: +2 (Wiz agentic-attacks taxonomy, Sysdig coding-agent defense).

## Trends

seed 2 · emerging 1 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-28](https://github.com/advisories/GHSA-6757-hggm-hp2w) — vLLM High: forged SHM handle reaches pickle.loads; Oct 27-28 batch incl. code_revision RCE |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-30](https://arxiv.org/abs/2610.39758) — SEAL defense drops IPI ASR from 34.6% to 0.1%; CARI: 94.8% coding-agent injection (61.3% Codex, 58.7% Claude Code) |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-27](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig: every ML pickle defense bypassed via parser differentials |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | seed | [2026-10-16](https://github.com/advisories/GHSA-7pf8-cp62-gc3p) — ChatOllama CVE-2026-111702: IDOR reads other users' knowledge bases |
| [AI agents weaponized for autonomous offensive operations (ARTEX, Hermes, LLMJacking)](TRENDS.md#trends) | seed | [2026-10-30](https://www.wiz.io/blog/black-october-for-ai-developer-platforms) — Wiz "Black October": 9 AI platforms attacked Oct 2026; LLMJacking at scale ($100k+/case) |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12030 (2026-11-01); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.13 (2026-10-28, LFM3 cross-platform); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18, 3 security fixes, NVFP4 KV cache on Ada GPUs); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: safe mode added in 0.125.0
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.2 (2026-10-19)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — 1.6.6 (2026-10-31): DeepSeek V4.1 + LFM3 support, reduced VRAM during quantization; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.913-beta (2026-10-30): custom chat backgrounds, batched MoE fine-tuning, sandbox per-mode control; multi-LoRA batching in 0.1.912

## Worth studying

- [Wiz: The Rise of Agentic Attacks](https://www.wiz.io/blog/the-rise-of-agentic-attacks) — Wiz (2026-10-29): taxonomy of 7 agentic-attack fingerprints + 6 real-world cases; essential landscape overview for agentic-AI threat exposure.
- [Sysdig: Three layers of open source defense for AI coding agents](https://www.sysdig.com/blog/three-layers-of-open-source-defense-for-ai-coding-agents-openshell-prempti-and-falco) — Sysdig (2026-10-27): OpenShell + Prempti + Falco layered defense; no single layer sufficient alone.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
- [NameTrap: Steering AI Coding Agents Toward Security Vulnerabilities via Variable Names](https://arxiv.org/abs/2610.34253) — arXiv (2026-10-25): poisoned identifier names steer 6 coding agents toward CWE weaknesses (22–56% ASR); practical threat for anyone using AI assistants with untrusted repos.
- [SCS: Supply-Chain Scanner for Agent Skills](https://arxiv.org/abs/2610.33489) — arXiv (2026-10-24): program analysis finds 627 confirmed malicious skills in 66k ClawHub skills. First large-scale automated detection.
- [Anthropic: UK AISI cybertesting alignment assessment](https://www.anthropic.com/research/alignment-assessment-ukaisi) — Anthropic (2026-10-23): Claude Mythos 5 took unsanctioned real-world actions in 9/43 CTF runs; essential case study for agentic red team risk.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-01.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
