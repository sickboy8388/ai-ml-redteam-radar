# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-11-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--23-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-23, daily)

- **No stage moves**: all three trends hold (inference-server emerging, agentic-injection emerging, supply-chain seed). Agentic-injection has the strongest accelerating signal — 4 new independent papers in 2 days.
- **AgentPhishing benchmark** (arXiv:2610.31404): adaptive phishing defeats 4/9 email agents (<10% detection, >45% compliance). Added as 10th evidence for agentic-injection.
- **Ollama SSRF** (CVE-2026-108836, Moderate, fixed 0.34.2) verified; inference-server evidence at 10/10 cap.
- **SGLang SafeUnpickler bypass** (CVE-2026-86793, CVSS 9.8): unauth RCE via pickle deserialization — queued pending primary GHSA verification. Would add a 7th independent project to the inference-server trend.
- **ChatOllama IDOR** (CVE-2026-111702, High) verified — strengthens the app-layer advisory cluster.
- **Major releases**: Ollama v0.40.9 (speech, d3 decision models), vLLM v0.32.0 (NVFP4 KV cache, security fixes), LocalAI v4.12.0, ExLlamaV3 v1.6.4, Unsloth v0.1.909 (DeepSeek-V4.1, multi-GPU training).

## Trends

seed 1 · emerging 2 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-12](https://github.com/advisories/GHSA-fr42-jr2w-mx59) — Ollama SSRF CVE-2026-108836; SGLang SafeUnpickler RCE queued |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-22](https://arxiv.org/abs/2610.31404) — AgentPhishing: 4/9 agents fail adaptive phishing; +3 agent-security papers |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-18](https://arxiv.org/abs/2610.21208) — support-persistent backdoors survive model reuse |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11835 (2026-10-23); SYCL multi-col matmul +5.9% tg128, MiniCPM-OCR 1.0, Nemotron GQA; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.9 (2026-10-22); speech gen with Phonon, d3 decision models (2B–27B), Flint 40B-MoE coding model (v0.40.8); security floor: ≥0.35.0 (CVE-2026-103663 path traversal), ≥0.34.2 (CVE-2026-108836 SSRF), ≥0.31.2 (CVE-2026-102697), ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18); NVFP4 KV cache, FP8 KV on SM100, Model Runner V2 default on ROCm, 3 security advisory fixes, tighter CORS default; security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.0 (2026-10-22); redesigned web UI, streaming voice, decision routing, persistent Qdrant vector stores
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16): hit@k attack success rate metric, Python 3.14 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08); 0.124.0 breaking: hosted ChatKit removed, explicit opt-in for many providers, Claude Opus 5.5 + GPT-6 Sol/Luna support
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.2 (2026-10-19); v5.20.0 (Oct 15) adds Muse Spark Open, Ling 3.0, UltraBERT, quantization during export
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); Azure/PyRIT archived 2026-03-27 (moved here)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.4 (2026-10-20); Nemotron 3.5 Bolt support, fairer prefill/decode scheduling, TP fixes
- **[Unsloth](https://github.com/unslothai/unsloth/releases)** — v0.1.909-beta (2026-10-19); DeepSeek-V4.1-Flash (552B/16B-active), FSDP2 multi-GPU LoRA/QLoRA alpha, `unsloth mcp add` one-command MCP setup, FLUX.3 image model

## Worth studying

- [AgentTriage: Replayable Security Diagnosis Across Heterogeneous Agent Runtimes](https://arxiv.org/abs/2610.30738) — Jie Ying et al. (2026-10-22): contract-based framework for grounded security claims across 5 agent runtimes, 0.858 diagnosis score, open-source; applicable to local agent setups.
- [Unsloth v0.1.909-beta: DeepSeek-V4.1 & multi-GPU training](https://github.com/unslothai/unsloth/releases) — unslothai (2026-10-19): DeepSeek-V4.1-Flash-1017 (552B/16B-active), FSDP2 multi-GPU LoRA/QLoRA alpha, one-command MCP setup. Core axis-1b tool.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-23.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
