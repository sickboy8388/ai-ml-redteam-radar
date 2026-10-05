# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-12-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--05-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-05)

- **41-day gap**: last scan was 2026-08-25; scheduled runs did not fire or persist (state-persistence blocker still open).
- **2 trends promoted seed→emerging**: [Self-hosted inference server attack surface](#trends) now has 8 evidence items from ≥6 independent orgs including in-the-wild exploitation (LMDeploy SSRF weaponized in 12h); [Agentic prompt-injection & agent-subsystem attacks](#trends) now has 8 evidence items including an impossibility result and a 92.5%-success hook-poisoning attack.
- **New SEED trend**: [AI model & pipeline supply-chain attacks](#trends) — Hugging Face breached by autonomous AI agent (Jul 2026), FaceHugger CVEs bypass trust_remote_code in HF diffusers, conjunctive poisoning of deployment artifacts, instruction backdoor attacks on coding LLMs.
- **Major tool releases**: llama.cpp b11405, Ollama v0.35.1 (Clef decision models), vLLM v0.31.0, LocalAI v4.11.0, garak v0.17.0 (EU AI Act mapping), promptfoo 0.123.1, transformers v5.18.0.
- **PyRIT archived**: Microsoft Azure/PyRIT archived 2026-03-27 — major red-team tooling gap.
- **ExLlamaV2 archived**: development moved to ExLlamaV3.
- **Queue**: +5 new items, 4 resolved/promoted → 12 live items.

## Trends

seed 1 · emerging 2 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-05](https://www.stingrai.io/blog/inference-server-security-vllm-triton-ollama-2026) — CVE roundup: Triton auth bypass 9.8, vLLM RCE 9.8, llama.cpp UAFs |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-02](https://arxiv.org/abs/2610.03448) — PI detector re-evaluation: benchmark scores mislead deployment |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-08-16](https://arxiv.org/abs/2608.15913) — Conjunctive Poisoning: deployment artifacts alter model behavior without weight modification |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11405 (2026-10-05); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.35.1 (2026-09-29, Clef decision models), v0.40.0-rc3 (2026-09-25, MLX runtime pre-release); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes); v4.10.0 (2026-09-17, fleet ops dashboard)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.123.1 (2026-09-18); 0.123.0 breaking change: GPT-5.6+ defaults to Responses API
- **[transformers](https://github.com/huggingface/transformers)** — v5.18.0 (2026-09-30, Nemotron 3 Diarization, HyperCLOVAX Vision V2, GTE)
- **[PyRIT](https://github.com/Azure/PyRIT)** — ARCHIVED (2026-03-27) — repository read-only, no releases
- **[ExLlamaV3](https://github.com/turboderp/exllamav3)** — successor to ExLlamaV2 (archived); ExLlamaV3 + TabbyAPI reportedly 30–60% faster than llama.cpp on Ampere/Ada

## Worth studying

- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): lifecycle hooks in agent harnesses are a blindspot — 92.5% compromise rate, 0% detection. Assess local agent setups with plugin/hook systems.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): systematic audit of llama.cpp; 5 of 10 bugs unpatched — essential for anyone running llama.cpp or red-teaming local deployments.
- [InjecMEM: Memory Injection Attack on LLM Agent Memory Systems](https://arxiv.org/abs/2608.23471) — arXiv (2026-08-24): agent memory is a demonstrated injection target — one interaction poisons later retrieval-conditioned answers.
- [llama.cpp v0.3.0](https://github.com/ggml-org/llama.cpp/releases/tag/v0.3.0) — ggml-org (2026-08-25): first v0.3.x tag — dots3-note multimodal, MTP, ggml v0.22.0.

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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-05.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
