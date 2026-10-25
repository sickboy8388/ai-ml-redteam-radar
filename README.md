# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-4-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-1-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-5-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--25-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-25, weekly recalibration W43)

- **Stage move**: agentic prompt-injection promoted emerging → **accelerating** (≥9 independent groups in 3 weeks, plus CVEs in shipping tools). Inference-server stays emerging; supply-chain stays seed.
- **New seed trend**: app-layer advisories in self-hosted LLM front-ends/gateways — Open WebUI (~20 advisories, fixed 0.11.4), Portkey AI Gateway SSRF, ChatOllama IDOR, Langflow SSRF, LightRAG XSS.
- **Supply chain**: Wiz reports malicious `litellm` 1.107.0 on PyPI/Docker (2026-10-21; last safe 1.106.2) — credential stealer aimed at cloud and AI-provider keys.
- **Ollama**: second /api/pull-path advisory (SSRF, CVE-2026-108836, fixed 0.34.2); llama.cpp b11871 hardens llama-server against deeply nested JSON.
- **Queue**: 5 live. **Daily sweeps did not run all week** (4th week, escalated).

## Trends

seed 2 · emerging 1 · accelerating 1 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-12](https://github.com/advisories/GHSA-fr42-jr2w-mx59) — Ollama Pull API SSRF (fixed 0.34.2); critical /api/pull traversal 10-08 |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-22](https://arxiv.org/abs/2610.31404) — AgentPhishing: email agents miss >90% of adaptive attacks |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-21](https://www.wiz.io/blog/litellm-compromised-steals-credentials) — malicious litellm 1.107.0 steals cloud and AI keys |
| [Self-hosted LLM front-end, gateway & RAG-UI advisories](TRENDS.md#trends) | seed | [2026-10-16](https://github.com/advisories/GHSA-7pf8-cp62-gc3p) — ChatOllama IDOR (CVSS4 8.7); Open WebUI batch 10-12 |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11871 (2026-10-25, rejects JSON nested >128 levels); b11405 (2026-10-05); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.11 (2026-10-24, speech endpoint, d3 decision models; no security fixes listed); v0.40.6 (2026-10-16); v0.40.0 (2026-09-25, MLX auto-runtime on Apple Silicon); security floor: ≥0.35.0 (CVE-2026-103663 path traversal), ≥0.34.2 (CVE-2026-108836 SSRF), ≥0.31.2 (CVE-2026-102697), ≥0.17.1 (CVE-2026-7482)
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
