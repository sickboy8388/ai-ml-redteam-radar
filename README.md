# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-9-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--13-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-13, daily)

- **Stage move: ai-supplychain-001 seed→emerging** — LiteLLM PyPI compromise (TeamPCP, Mar 2026) verified as first in-the-wild supply-chain attack on AI/LLM proxy infrastructure; two new backdoor papers (PersistBD, answer-side backdoors) bring evidence to 8/10 from ≥7 independent sources.
- **agentic-injection-001 +2 evidence** (now 10/10): APEX skill-chaining hijack (74.2% across 6 models) and LLMLeak web-fetch exfiltration (79.7% across 11 models). Held at emerging.
- **New queue items**: Ollama 27-vuln independent audit, MITRE ATLAS v2026.09 (agentic AI techniques), Wiz "State of AI in Cloud 2026" (MCP in 80% of environments), ZoneClaw memory-zoning defense, arXiv October agent-security paper cluster (≥15 papers).
- **Tool updates**: llama.cpp b11580, Ollama v0.40.3, promptfoo 0.124.1, Unsloth v0.1.906-beta.
- **Study pick**: PersistBD — backdoors survive fine-tuning + RL in coding agents (EMNLP 2026).

## Trends

seed 0 · emerging 3 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-05](https://www.stingrai.io/blog/inference-server-security-vllm-triton-ollama-2026) — CVE roundup: Triton auth bypass 9.8, vLLM RCE 9.8, llama.cpp UAFs |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-02](https://arxiv.org/abs/2610.03448) — PI detector re-evaluation: benchmark scores mislead deployment |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts, package hijacks)](TRENDS.md#trends) | emerging | [2026-10-06](https://arxiv.org/abs/2610.07723) — Answer-side backdoor: self-generated trigger bypasses refusal; near-100% ASR |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11580 (2026-10-13); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.3 (2026-10-11), v0.40.4-rc1 (2026-10-12, decision models, EmbeddingGemma 2); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes); v4.10.0 (2026-09-17, fleet ops dashboard)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08): Claude Opus/Sonnet 5.5, GPT-6 support, isolated workspaces for coding agents
- **[transformers](https://github.com/huggingface/transformers)** — v5.18.0 (2026-09-30, Nemotron 3 Diarization, HyperCLOVAX Vision V2, GTE)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); v1.0.0 (Jul 24) new architecture; Azure/PyRIT archived 2026-03-27 (moved here)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — EXL3 quant + inference library for consumer GPUs, MoE CPU offload, TabbyAPI backend; speed claims unverified
- **[Unsloth](https://github.com/unslothai/unsloth)** — v0.1.906-beta (2026-10-12): browser use, decision model training, consumer GPU layer offload (7 GiB for 8B 4-bit), AMD RX support, MoE GGUF speedups

## Worth studying

- [PersistBD: Backdoor Persistence in LLM Agent Post-Training](https://arxiv.org/abs/2610.07510) — EMNLP 2026 Findings (2026-10-05): backdoors in third-party models survive SFT+RL; attack success rises from 20%→76%. Critical for anyone fine-tuning or adapting third-party models into coding agents.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-13.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
