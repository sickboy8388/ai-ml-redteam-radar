# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-1-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-8-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--12-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-12)

- **Agentic injection → accelerating**: 2 new evidence items — ToFu (273 MCP servers fuzzed, 253 verified bugs in 118 servers) and cross-session skill attacks (46.7–77.4% ASR across Codex CLI, Gemini CLI, Claude Code). ≥10 independent research groups, attack surface still expanding.
- **AI supply chain seed → emerging**: 2 new evidence items — empirical study of 16,977 flagged HF models (22.1% actively referenced in 21,000+ code locations with zero provenance checks) and cryptographic proof that models can provably hide arbitrary capabilities.
- **Inference servers held at emerging**: 8 new vLLM GHSA advisories (Trail of Bits / OpenAI "Patch the Planet" audit, mostly Moderate); no new critical-severity items.
- **Queue**: +5 new items (Langflow Critical RCE, fsspec SSTI, MITRE ATLAS agentic update, vLLM audit cluster, reward-hacking contagion); 2 resolved (Ollama MLX shipped, Unsloth verified).
- **Study picks**: ToFu MCP fuzzer; Unsloth MoE fine-tuning update (axis 1b).

## Trends

seed 0 · emerging 2 · accelerating 1 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-09](https://arxiv.org/abs/2610.13651) — ToFu: 273 MCP servers fuzzed, 253 verified semantic security bugs in 118 servers |
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-05](https://www.stingrai.io/blog/inference-server-security-vllm-triton-ollama-2026) — CVE roundup: Triton auth bypass 9.8, vLLM RCE 9.8, llama.cpp UAFs |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-09](https://arxiv.org/abs/2610.12893) — 16,977 flagged HF models, 22.1% actively referenced, zero provenance verification |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11564 (2026-10-12); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.3 (2026-10-11, launch improvements), v0.40.2 (2026-10-08, background model upgrade); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778); 8 new Moderate GHSAs from Trail of Bits / OpenAI audit (Oct 5-6)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, failover chains, signed OCI galleries)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08); 0.124.0 adds Claude Opus 5.5, GPT-6 Sol/Luna support; Sharp/Codex SDK security patches
- **[transformers](https://github.com/huggingface/transformers)** — v5.19.0 (2026-10-06, EmbeddingGemma2, MoE router logits, continuous batching for SDPA/flash)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); Best-of-N scanner, multilingual/audio capabilities, 488 in-the-wild jailbreak templates
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — EXL3 quant + inference library for consumer GPUs, MoE CPU offload, TabbyAPI backend; speed claims unverified

## Worth studying

- [ToFu: Exploiting and Fuzzing the LLM-Orchestrator-Tool Trust Boundary](https://arxiv.org/abs/2610.13651) — arXiv (2026-10-09): 273 MCP servers fuzzed, 253 verified bugs in 118 servers. Essential for anyone deploying or auditing MCP tooling.
- [Unsloth 2026 Update — Faster MoE](https://unslothai.substack.com/p/unsloth-2026-update-faster-moe) — Unsloth AI (2026-02-10): 12x faster MoE training, >35% less VRAM; relevant for consumer-GPU fine-tuning (axis 1b).
- [ExLlamaV3](https://github.com/turboderp-org/exllamav3) — turboderp-org (accessed 2026-10-11): EXL3 quantization + inference for consumer GPUs with MoE CPU offload; fits a 12GB RTX 4070 Ti.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-12.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
