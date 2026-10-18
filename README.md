# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-7-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--18-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-18, weekly recalibration W42)

- **No stage moves**: inference-server and agentic-injection stay emerging (agentic is the likeliest to accelerate next); supply-chain stays seed.
- **Ollama**: critical unauth path traversal in /api/pull (CVE-2026-103663, CVSS4 9.4; fixed 0.35.0 per advisory text) and an agent bash-approval bypass via prompt injection (CVE-2026-102697; fixed 0.31.2). Both GHSA-unreviewed.
- **Agentic**: Decepticon CVE-2026-61732 (ChatML token role forgery against self-hosted backends, CVSS 10.0), plus new MCP and indirect-injection papers.
- **Unsloth** v0.1.904–908 verified: QLoRA MoE speedups are measured on datacenter GPUs (flagged for the 12GB envelope).
- **Queue**: 7 live; new candidate trend (app-layer advisories in self-hosted LLM front-ends/gateways). **Daily sweeps did not run all week** (escalated).

## Trends

seed 1 · emerging 2 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-08](https://github.com/advisories/GHSA-w8p2-phwr-px3r) — Ollama /api/pull path traversal, CVSS4 9.4, unauth |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-18](https://arxiv.org/abs/2610.22301) — MCP filesystem capability laundering at scale; Decepticon CVSS 10.0 role forgery |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-18](https://arxiv.org/abs/2610.21208) — support-persistent backdoors survive model reuse |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11405 (2026-10-05); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.6 (2026-10-16); v0.40.0 (2026-09-25, MLX auto-runtime on Apple Silicon); security floor: ≥0.35.0 (CVE-2026-103663 path traversal), ≥0.31.2 (CVE-2026-102697), ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes); v4.10.0 (2026-09-17, fleet ops dashboard)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.123.1 (2026-09-18); 0.123.0 breaking change: GPT-5.6+ defaults to Responses API
- **[transformers](https://github.com/huggingface/transformers)** — v5.18.0 (2026-09-30, Nemotron 3 Diarization, HyperCLOVAX Vision V2, GTE)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); v1.0.0 (Jul 24) new architecture; Azure/PyRIT archived 2026-03-27 (moved here)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — EXL3 quant + inference library for consumer GPUs, MoE CPU offload, TabbyAPI backend; speed claims unverified

## Worth studying

- [Unsloth releases (v0.1.904–0.1.908)](https://github.com/unslothai/unsloth/releases) — unslothai (2026-10-15): local fine-tune + inference studio — OS-level sandboxing for model-run code, browser-use, QLoRA MoE speedups (measured on datacenter GPUs; no independent benchmarks).
- [ExLlamaV3](https://github.com/turboderp-org/exllamav3) — turboderp-org (accessed 2026-10-11): EXL3 quantization + inference for consumer GPUs with MoE CPU offload; fits a 12GB RTX 4070 Ti.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): systematic audit of llama.cpp; 5 of 10 bugs unpatched — essential for anyone running llama.cpp or red-teaming local deployments.

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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-05.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
