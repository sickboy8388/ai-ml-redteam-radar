# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-4-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-1-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-2-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--21-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-21, daily update)

- **Agentic injection → accelerating**: single-day arXiv listing yielded 9+ independent papers on agentic attacks/defenses; authorization composability impossibility result added as 10th evidence item. Research community convergence from multiple angles.
- **New seed trend: LLM front-end/gateway app-layer vulns** (`llm-frontend-001`): 25+ CVEs across ≥5 independent projects (Open WebUI 19-CVE batch, ChatOllama IDOR, Portkey SSRF, Langflow cross-user hijack, 9router config injection). The web app layer between users and inference backends is now a tracked attack surface.
- **Tool releases**: llama.cpp b11785 (WebSocket auth, MoE scaling), Ollama v0.40.7 (pplx-decider), vLLM v0.32.0 (FP8 KV cache, CORS fix), Unsloth v0.1.909-beta (multi-GPU FSDP2, Vulkan non-NVIDIA).
- **Queue**: 2 live items (MITRE ATLAS v5.4.0 verification, RedThread red-team CLI).

## Trends

seed 2 · emerging 1 · accelerating 1 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-20](https://arxiv.org/abs/2610.27620) — authorization composability impossibility for LLM agents; 9+ independent papers in single listing |
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-08](https://github.com/advisories/GHSA-w8p2-phwr-px3r) — Ollama /api/pull path traversal, CVSS4 9.4, unauth |
| [Self-hosted LLM front-end/gateway app-layer vulnerabilities](TRENDS.md#trends) | seed | [2026-10-20](https://github.com/advisories/GHSA-qf42-fp6f-25w9) — 25+ CVEs across Open WebUI, ChatOllama, Portkey, Langflow, 9router |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-18](https://arxiv.org/abs/2610.21208) — support-persistent backdoors survive model reuse |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11785 (2026-10-21); b11780 adds WebSocket auth middleware; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.7 (2026-10-18, pplx-decider 27B, spec decoding improvements); security floor: ≥0.35.0 (CVE-2026-103663 path traversal), ≥0.34.2 (CVE-2026-108836 SSRF), ≥0.31.2 (CVE-2026-102697), ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18, FP8 KV cache default for GLM-5.x halves KV memory, CORS-allow-all removed); security floor: ≥0.26.0 (CVE-2026-73560 SSRF), ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes); v4.10.0 (2026-09-17, fleet ops dashboard)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16): hit@k attack success metric, Python 3.14 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08); 0.123.0 breaking change: GPT-5.6+ defaults to Responses API
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.2 (2026-10-19, multimodal generate fix, bfloat16 MoE gradient fix)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); v1.0.0 (Jul 24) new architecture; Azure/PyRIT archived 2026-03-27 (moved here)
- **[Unsloth](https://github.com/unslothai/unsloth)** — v0.1.909-beta (2026-10-19): multi-GPU FSDP2 (alpha), Vulkan inference for non-NVIDIA GPUs, adamw_flash optimizer, LoRA dropout on fused kernels 28% faster/step
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v0.0.6; EXL3 quant + inference library for consumer GPUs, MoE CPU offload, TabbyAPI backend; now covers DeepSeek V4, Gemma 4, Qwen 3.5 MoE
- **[Open WebUI](https://github.com/open-webui/open-webui)** — ≥0.11.4 required (19 CVEs patched in batch disclosure 2026-10-12)

## Worth studying

- [CarryoverBench: Benchmarking Carryover Attacks on LLM Agents](https://arxiv.org/abs/2610.28425) — Xu et al. (2026-10-20): persistent-memory carryover attacks re-fire across sessions without decay; directly relevant to local agent setups.
- [AgenticVulHunter: Local Agentic Vulnerability Hunting](https://arxiv.org/abs/2610.27383) — Abhishek et al. (2026-10-19): local agentic vuln hunting with open-weight models; 23.8% accuracy on multi-file detection.
- [Unsloth releases (v0.1.904–0.1.909)](https://github.com/unslothai/unsloth/releases) — unslothai (2026-10-19): local fine-tune + inference studio — multi-GPU FSDP2, Vulkan non-NVIDIA, QLoRA MoE speedups (datacenter-measured; no independent benchmarks).
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-21.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
