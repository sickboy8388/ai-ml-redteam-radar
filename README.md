# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-1-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-8-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--16-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-16, daily update)

- **Stage move**: agentic-injection-001 promoted **emerging → accelerating** on new independent evidence — MCP filesystem capability laundering (16.4% of servers exploitable, 2 CVEs) and Claude Code plugin hash-pin bypass (CVE-2026-86063, CVSS 7.5). 10/10 evidence slots filled from ≥10 independent groups.
- **New evidence**: support-persistent backdoors surviving clean-data distillation added to supply-chain trend (now 6/10 evidence).
- **Major releases**: llama.cpp v0.7.0 (MoE expert cache, speculative decoding, new port 9931), Ollama v0.40.5 stable (MLX, Nemotron 3.5 Super/Bolt), ExLlamaV3 v1.6.2 (ROCm support), transformers v5.20.0.
- **OWASP verified**: GenAI LLM Top 10 2026 confirmed via CSA (Aug 3 pub); Excessive Agency up to #3, Agent Control Standard v0.1 unveiled.
- **Queue**: 8 live items including HNSW RAG poisoning, INFUSE IPI benchmark, PI detection calibration.

## Trends

seed 1 · emerging 1 · accelerating 1 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-15](https://arxiv.org/abs/2610.22301) — MCP filesystem capability laundering: 16.4% of 4,806 servers exploitable; 2 CVEs in Anthropic's Git MCP Server |
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-05](https://www.stingrai.io/blog/inference-server-security-vllm-triton-ollama-2026) — CVE roundup: Triton auth bypass 9.8, vLLM RCE 9.8, llama.cpp UAFs |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-15](https://arxiv.org/abs/2610.21208) — Support-persistent backdoors survive clean-data distillation with >96% ASR |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — v0.7.0 (2026-10-15): MoE expert cache (~2.2x decode speedup), LiliCorr speculative decoding, new default port 9931, OOB fixes, stricter UTF-8; security floor: ≥b9061 (CVE-2026-43631 UAF)
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.5 (2026-10-14, Nemotron 3.5 Super/Bolt, cloud decision models), v0.40.1-v0.40.4 (Oct 7-12, MLX decision models, background model upgrades); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, decision models); v4.10.0 (2026-09-17, fleet ops dashboard, 4 CVE fixes)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.2 (2026-10-14): ROCm support (gfx1100+), faster CPU offload, Turing + AVX2 optimizations; EXL3 quant for consumer GPUs
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08): cost recording, OpenAI Decisions; 0.124.0 breaking: several SDKs now opt-in
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.0 (2026-10-15, Muse Spark Open, Nemotron 3.5, UltraBERT, expert-parallel export); v5.19.0 (2026-10-06, EmbeddingGemma2)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04): undetermined scores, 488 jailbreak templates, scanner capabilities
- **[Unsloth](https://github.com/unslothai/unsloth)** — v0.1.908-beta (2026-10-15): Nemotron 3.5, diffusion LLM training, browser use, decision models; platform expanded well beyond fine-tuning

## Worth studying

- [MCP Filesystem Capability Laundering at Scale](https://arxiv.org/abs/2610.22301) — arXiv (2026-10-15): 16.4% of MCP servers have undeclared filesystem access; 150 confirmed exploitable. Audit your MCP deployments.
- [ExLlamaV3 v1.6.2](https://github.com/turboderp-org/exllamav3) — turboderp-org (2026-10-14): ROCm support, faster CPU offload, Turing optimizations. EXL3 quant fits a 12GB RTX 4070 Ti.
- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): 92.5% compromise rate across 7 harnesses, 0% detection. Assess local agent setups.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): 5 of 10 bugs unpatched. Essential for llama.cpp deployments.

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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-16.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
