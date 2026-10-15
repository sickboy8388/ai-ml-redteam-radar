# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-1-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-9-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--15-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-15, daily)

- **Stage move: agentic-injection-001 emerging→accelerating** — Decepticon ChatML injection (CVE-2026-61732, CVSS 10.0) demonstrates role-boundary forgery via web crawl content on vLLM/Ollama/LM Studio backends; MCP SDK OAuth credential theft (CVE-2026-104850, CVSS 7.5) enables token exfiltration without user interaction; 4 new independent October papers (Kairos, BrowseSafe++, TRAP, AgentSafeEvo) confirm sustained multi-org research acceleration.
- **local-inference-001**: +1 evidence — vLLM CVE-2026-73558 cross-user data leak via integer overflow (CVSS 5.3, fixed v0.27.0); new attack class (confidentiality breach in shared inference batches); 10/10 evidence slots full.
- **ai-supplychain-001**: +1 evidence — LMDeploy CVE-2025-66455 pickle-deserialization RCE (CVSS 9.8) in DistServe ZMQ transport; held at seed.
- **Queue**: +6 new items (Langflow MCP RCE cluster, PraisonAI agent RCE cluster, OWASP LLM Top 10 2026 confirmed, MITRE ATLAS v2026.09, NLTK pickle bypass, LMDeploy companion CVE); 1 resolved, 1 dropped (Hydra stale); 9 live items.
- **Tool releases**: Ollama v0.40.4 (decision models, MLX runner GA), llama.cpp b11642, vLLM v0.31.0, transformers v5.19.0, promptfoo 0.124.1, PyRIT v1.1.0.

## Trends

seed 1 · emerging 1 · accelerating 1 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-06](https://github.com/advisories/GHSA-6qxp-vccf-f47h) — MCP SDK OAuth credential theft CVE-2026-104850 CVSS 7.5 |
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-09-08](https://github.com/advisories/GHSA-7m6h-x95x-82q5) — vLLM CVE-2026-73558 cross-user data leak in inference batches |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-09-18](https://github.com/advisories/GHSA-2vh9-42vm-xmv2) — LMDeploy pickle-deserialization RCE CVSS 9.8 via ZMQ transport |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11642 (2026-10-15); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.4 (2026-10-12, decision models, MLX runner, multimodal embeddings), v0.40.5-rc0 (2026-10-14 pre-release); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.27.0 (CVE-2026-73558 data leak), ≥0.22.0 (CVE-2026-41523 RCE)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, model failover chains, signed OCI galleries)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08); 0.124.0 breaking: removed hosted ChatKit provider, SDKs opt-in
- **[transformers](https://github.com/huggingface/transformers)** — v5.19.0 (2026-10-06, EmbeddingGemma2 multimodal, expert parallelism token-dispatch, quantized cache fixes)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04): Best-of-N, split-payload, multilingual scanner; ShieldGemma scorer; 488 TrustAIRLab jailbreak templates
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — EXL3 quant + inference library for consumer GPUs, MoE CPU offload, TabbyAPI backend; speed claims unverified

## Worth studying

- [Kairos: Transactional Security Enforcement at the System Boundary for LLM Agents](https://arxiv.org/abs/2610.18457) — arXiv (2026-10-13): reference monitor for opaque agents; defers ambiguous effects, uses bounded oracles; reduces AgentDojo attack success 47.0%→2.7%. Practical defense for local agent deployments.
- [TRAP: Tree-Guided Reinforcement-Augmented Probing for Automated LLM Jailbreaking](https://arxiv.org/abs/2610.17313) — arXiv (2026-10-12): hierarchical RL for black-box automated jailbreaking; 45.6–97.9% ASR on 7 models. Useful for red-team automation assessment.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-15.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
