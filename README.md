# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-2-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--18-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-18, daily + weekly W42)

- **Agentic injection**: +1 evidence (PackHallu rule-file injection); 6 more October papers opened (MetaCascade, COPEX, Innocent Courier, MemForm, SkillScreen); sustained multi-org burst — strongest active axis.
- **Inference servers**: evidence full 10/10; additional verified: Ollama CVE-2026-108836 SSRF (Moderate, fixed 0.34.2); vLLM v0.32.0 ships 3 security fixes incl. CVE-2026-73560 SSRF.
- **vLLM v0.32.0** (Oct 18): 3 security fixes, drops Python 3.10, restricts default CORS origins, lower-precision KV cache support.
- **garak v0.17.1** (Oct 16): hit@k metric, Python 3.14, tighter detector scoring.
- **Unsloth v0.1.908** (Oct 15): Nemotron 3.5, DeepSpeed ZeRO, MCP security restriction.
- **Queue**: 2 live items; app-layer advisory cluster partially verified (Langflow SSRF opened, 4 others via web search).

## Trends

seed 1 · emerging 2 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-08](https://github.com/advisories/GHSA-w8p2-phwr-px3r) — Ollama /api/pull path traversal, CVSS4 9.4; vLLM v0.32.0 3 security fixes |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-18](https://arxiv.org/abs/2610.22301) — MCP capability laundering + PackHallu rule-file injection; 15+ papers in Oct |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-18](https://arxiv.org/abs/2610.21208) — support-persistent backdoors survive model reuse |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11718 (2026-10-18); HF Hub model discovery in UI (b11714), Hexagon NPU support, CUDA MoE fusion; security floor: ≥b9061 (CVE-2026-43631); 5/10 Cyera bugs unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.7-rc0 (2026-10-18); v0.40.6 (Oct 16); decision models, cloud features; security floor: ≥0.35.0 (CVE-2026-103663), ≥0.34.2 (CVE-2026-108836 SSRF), ≥0.31.2 (CVE-2026-102697), ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18): 3 security fixes (SSRF CVE-2026-73560, tokenizer, ZMQ exhaustion), CORS hardening, drops Python 3.10; security floor: ≥0.32.0, ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02): decision models, signed OCI galleries, safer API behavior
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16): hit@k metric, Python 3.14, tighter detectors; v0.17.0 (Sep 9): EU AI Act mapping
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.123.1 (2026-09-18); 0.123.0 breaking: GPT-5.6+ defaults to Responses API
- **[transformers](https://github.com/huggingface/transformers)** — v5.18.0 (2026-09-30)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); v1.0.0 (Jul 24); Azure/PyRIT archived 2026-03-27
- **[Unsloth](https://github.com/unslothai/unsloth)** — v0.1.908-beta (2026-10-15): Nemotron 3.5, DeepSpeed ZeRO, MCP security fix; v0.1.905: OS-level sandboxing for model-run code
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — EXL3 quant + inference for consumer GPUs, MoE CPU offload, TabbyAPI backend; speed claims unverified

## Worth studying

- [COPEX: Benchmarking LLM Robustness Across MCP Layers](https://arxiv.org/abs/2610.04378) — Birhan et al. (2026-10-03): 64.4% mean attack success across 25 attack types and 9 models in MCP systems; combined input+context scanning cuts success by 49.6%.
- [Unsloth releases (v0.1.904–0.1.908)](https://github.com/unslothai/unsloth/releases) — unslothai (2026-10-15): local fine-tune + inference studio — OS-level sandboxing, QLoRA MoE speedups (datacenter GPUs; no independent benchmarks).
- [ExLlamaV3](https://github.com/turboderp-org/exllamav3) — turboderp-org (accessed 2026-10-11): EXL3 quantization + inference for consumer GPUs with MoE CPU offload; fits a 12GB RTX 4070 Ti.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): 10 llama.cpp vulnerabilities; 5 unpatched — essential for running or red-teaming local deployments.

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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-18.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
