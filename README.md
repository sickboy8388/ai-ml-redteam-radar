# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-8-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--11-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-11, daily)

- **No stage moves**: all three trends hold (inference-server and agentic-injection at emerging; supply-chain at seed).
- **+4 evidence items**: SGLang CVE-2026-5760 CVSS 9.8 (gap fill, inference-server trend); NOMOS compiled tool-call gates and PyCache Trap skill scanner bypass (agentic-injection); DITTO pickle scanner on 10k+ HF repos (supply-chain).
- **8 new arXiv papers opened** (Oct 7-8): prompt injection defenses (LTBD), guardrail bypass (BRANCH), speculative-decoding attacks (Speedbumps), RAG security meta-model, agent security incidents framework (PASAC), and more.
- **Tool releases**: llama.cpp b11552 (Oct 10), Ollama v0.40.3 stable (Oct 11), promptfoo 0.124.1 (Oct 8), transformers v5.19.0 (Oct 6), ExLlamaV3 v1.6.1 (Oct 10).
- **Queue**: 8 live items; +4 new observations (Speedbumps, BRANCH, RAG meta-model, PASAC).

## Trends

seed 1 · emerging 2 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-05](https://www.stingrai.io/blog/inference-server-security-vllm-triton-ollama-2026) — CVE roundup: Triton auth bypass 9.8, vLLM RCE 9.8, llama.cpp UAFs; +SGLang CVE-2026-5760 gap fill |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-08](https://arxiv.org/abs/2610.11030) — NOMOS: compiled tool-call gates achieve 0% ASR on AgentDojo banking |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-07](https://arxiv.org/abs/2610.10735) — DITTO: 9.3% of top HF repos still use unsafe pickle; 100% detection scanner |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11552 (2026-10-10); MiniCPM-V 4.7, MoE OpenCL kernels, server slot-wait fix; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.3 (2026-10-11, background model upgrades, cloud model proxy); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, failover chains, signed OCI galleries)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08); 0.124.0: Claude Opus/Sonnet 5.5, GPT-6/6.1, isolated coding-agent workspaces; breaking: several integrations now opt-in
- **[transformers](https://github.com/huggingface/transformers)** — v5.19.0 (2026-10-06, EmbeddingGemma2 multimodal embeddings, expert parallelism, cache fixes)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); v1.0.0 (Jul 24) new architecture; Azure/PyRIT archived 2026-03-27 (moved here)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.1 (2026-10-10): recurrent draft models, lower VRAM drafting, ROCm support (v1.6.0), token-embedding quantization (v1.5.4); consumer GPU focused

## Worth studying

- [DITTO: Context-aware Pickle-based Pre-Trained Model Scanner](https://arxiv.org/abs/2610.10735) — arXiv (2026-10-07): practical scanner for auditing pickle-serialized models on HuggingFace; 9.3% of top repos still use unsafe pickle; 100% detection at 0.7% FPR.
- [ExLlamaV3 v1.6.1](https://github.com/turboderp-org/exllamav3/releases) — turboderp-org (2026-10-10): very active development — recurrent draft models, ROCm support, token-embedding quantization; natural fit for 12GB RTX 4070 Ti.
- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): lifecycle hooks in agent harnesses are a blindspot — 92.5% compromise rate, 0% detection. Assess local agent setups with plugin/hook systems.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-11.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
