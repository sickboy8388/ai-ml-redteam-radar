# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-4-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-1-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-12-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--19-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-19, daily)

- **Stage move**: agentic-injection emerging→**accelerating** — 10 evidence items across ≥9 independent groups; CVEs + impossibility result + dedicated red-team tooling (ASPIRE) confirm sustained acceleration.
- **New seed trend**: **frontend-appstack-001** — self-hosted LLM front-end & gateway app-layer vulnerabilities. Open WebUI had 19+ CVEs published Oct 12-16 (privilege escalation, XSS, authz bypass); Langflow SSRF; ChatOllama IDOR; Portkey AI Gateway SSRF. 4 independent projects confirmed.
- **LMCache CVE-2026-105192** (Critical, CVSS 9.8): unauth pickle deserialization RCE in vLLM KV-cache layer; public PoC; fixed 0.5.6. Added to local-inference-001.
- **Tool releases**: llama.cpp b11724, Ollama v0.40.6, vLLM v0.32.0, ExLlamaV3 v1.6.3, garak v0.17.1, promptfoo v0.124.1, Unsloth v0.1.908, transformers v5.20.1.
- **Queue**: 12 live items; 3 resolved, 5 new.

## Trends

seed 2 · emerging 1 · accelerating 1 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-16](https://github.com/advisories/GHSA-w5f2-9q9c-ff4h) — LMCache pickle RCE in vLLM KV-cache layer, CVSS 9.8, public PoC |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | **accelerating** | [2026-10-06](https://arxiv.org/abs/2610.08951) — ASPIRE: agentic red-teaming engine for prompt-injection discovery |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-18](https://arxiv.org/abs/2610.21208) — support-persistent backdoors survive model reuse |
| [Self-hosted LLM front-end & gateway app-layer vulnerabilities](TRENDS.md#trends) | **seed (new)** | [2026-10-16](https://github.com/advisories/GHSA-7pf8-cp62-gc3p) — ChatOllama IDOR exposes private knowledge bases; Open WebUI 19+ CVEs |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11724 (2026-10-19); Q1_0/Q2_0 quant, Hexagon backend, CUDA flash-attn fixes; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.6 (2026-10-16); decision models (clef), q2_0 GGUF, background model upgrades; security floor: ≥0.35.0 (CVE-2026-103663 path traversal), ≥0.34.2 (CVE-2026-108836 SSRF), ≥0.31.2 (CVE-2026-102697 agent bypass)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18, NVFP4 KV cache, GPU n-gram speculator, CORS fix); security floor: ≥0.29.0 (CVE-2026-109311 FFmpeg heap overflow), ≥0.22.0 (CVE-2026-41523)
- **[LMCache](https://github.com/advisories/GHSA-w5f2-9q9c-ff4h)** — security floor: ≥0.5.6 (CVE-2026-105192 pickle RCE, CVSS 9.8); check multi-node/K8s ZeroMQ bindings
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, decision models, signed OCI galleries, audio scenes)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.3 (2026-10-17); ROCm support, faster CPU offload, hybrid drafting, lower VRAM overhead; fits 12GB RTX 4070 Ti
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16): hit@k attack success rate metric, Python 3.14
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08); OpenAI Decisions support, Codex security paths
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.1 (2026-10-16, Beam coding model, Muse Spark Open MoE); v5.19.0 (2026-10-06, EmbeddingGemma2)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); Best-of-N + split-payload scanners, 488 jailbreak templates; no October release
- **[Unsloth](https://github.com/unslothai/unsloth)** — v0.1.908 (2026-10-15): Nemotron 3.5, prompt caching for coding agents, DeepSpeed ZeRO-2/3, browser-use expansion

## Worth studying

- [ExLlamaV3 v1.6.0–v1.6.3](https://github.com/turboderp-org/exllamav3/releases) — turboderp-org (2026-10-07..17): 4 releases in 10 days — ROCm support (gfx1100+), faster CPU offloading + core pinning, hybrid drafting (draft model + long-ngram), tensor-parallel DFlash2. The natural 12GB RTX 4070 Ti inference backend (axis 1b).
- [garak v0.17.1](https://github.com/NVIDIA/garak/releases) — NVIDIA (2026-10-16): hit@k attack success rate metric for red-team evals; Python 3.14; detector fixes. Practical red-team tooling update.
- [Unsloth releases (v0.1.907–0.1.908)](https://github.com/unslothai/unsloth/releases) — unslothai (2026-10-13..15): prompt caching for coding agents running local GGUFs, DeepSpeed ZeRO-2/3 training, browser-use expansion. Core axis-1b tool.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-19.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
