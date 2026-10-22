# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-1-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-10-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--22-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-22, daily sweep)

- **local-inference-001 emerging → accelerating**: LMCache CVE-2026-105192 (Critical 9.8, pickle RCE in distributed KV cache layer, JFrog disclosure + public PoC) meets the weekly's condition — a second org/project with a critical. Attack surface now spans inference servers AND the cache sharing layer beneath them.
- **vLLM v0.32.0** ships 3 security advisories + CORS hardened to deny-by-default + image-format restrictions + HMAC-signed multimodal cache handles.
- **Ollama CVE-2026-108836**: SSRF in Pull API via IsValid bypass (Moderate, fixed 0.34.2, public exploit).
- **Agentic injection**: APEX skill-chain hijacking paper (74.2% success across 6 models) added; 4 more independent groups found in one sweep — strongest candidate for accelerating.
- **ExLlamaV3** v1.6.0–1.6.4: ROCm support, tensor-parallel DFlash2, hybrid drafting — major consumer GPU progress.
- **Queue**: 10 live items; Open WebUI CVE cluster confirmed (≥7 CVEs via secondary, primaries pending).

## Trends

seed 1 · emerging 1 · accelerating 1 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs, distributed cache)](TRENDS.md#trends) | **accelerating** | [2026-10-16](https://github.com/advisories/GHSA-w5f2-9q9c-ff4h) — LMCache pickle RCE CVSS 9.8 in distributed KV cache; JFrog PoC |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-18](https://arxiv.org/abs/2610.22301) — MCP capability laundering; APEX skill-chain hijack 74.2%; Decepticon CVSS 10.0 |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-18](https://arxiv.org/abs/2610.21208) — support-persistent backdoors survive model reuse |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11809 (2026-10-22); SenseNova U1, Flint model, WebGPU Q2_0 dequant; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.8 (2026-10-21, Flint 40B MoE 262K ctx); v0.40.7 (Oct 18, pplx-decider 27B); security floor: ≥0.35.0 (CVE-2026-103663 path traversal), ≥0.34.2 (CVE-2026-108836 SSRF), ≥0.31.2 (CVE-2026-102697), ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18): 3 security fixes, CORS deny-by-default, NVFP4/FP8 KV cache on SM8x/SM12x/SM90, EmbeddingGemma 2, MiniCPM-V 4.7; security floor: ≥0.32.0 (3 GHSAs), ≥0.22.0 (CVE-2026-41523)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes); v4.10.0 (2026-09-17, fleet ops dashboard)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16): hit@k attack success metric, Python 3.14 support, detector fixes
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08): security dep patches, isolated workspaces for coding agents; 0.124.0 breaking: SDKs opt-in, new model support
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.2 (2026-10-19); v5.20.0 (Oct 15, Muse Spark 816B MoE, Ling 3.0 Flash, quantization during export)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); v1.0.0 (Jul 24) new architecture; Azure/PyRIT archived 2026-03-27 (moved here)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.4 (2026-10-20): ROCm support (gfx1100+), tensor-parallel DFlash2, recurrent draft models, hybrid drafting, Turing/AVX2 optimizations; fits 12GB VRAM
- **[Unsloth](https://github.com/unslothai/unsloth)** — v0.1.909 (2026-10-19): DeepSeek-V4.1-Flash, FSDP2 multi-GPU (alpha), Vulkan GGUF (no NVIDIA GPU required), context parallelism
- **[LMCache](https://github.com/LMCache/LMCache)** — 0.5.6 (2026-10-16): CRITICAL — upgrade from ≤0.5.5 (CVE-2026-105192, pickle RCE in ZeroMQ transport, public PoC)

## Worth studying

- [LMCache CVE-2026-105192 — pickle RCE in distributed inference cache](https://github.com/advisories/GHSA-w5f2-9q9c-ff4h) — JFrog/GHSA (2026-10-16): unauthenticated RCE via pickle deserialization on ZeroMQ transport in LMCache (vLLM KV cache sharing); public PoC; CVSS 9.8. Essential reading for distributed inference.
- [vLLM v0.32.0 security hardening](https://github.com/vllm-project/vllm/releases/tag/v0.32.0) — vllm-project (2026-10-18): 3 GHSAs fixed, CORS deny-by-default, image format restrictions, HMAC-signed cache. Reference for securing local vLLM deployments.
- [ExLlamaV3 v1.6.0–1.6.4](https://github.com/turboderp-org/exllamav3) — turboderp-org (2026-10-20): ROCm, faster CPU offload, hybrid drafting; ideal for a 12GB RTX 4070 Ti.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-22.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
