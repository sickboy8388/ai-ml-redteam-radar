# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-13-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--09-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-09)

- **1 trend promoted seed→emerging**: [AI model & pipeline supply-chain attacks](#trends) now has 6 evidence items from ≥6 independent orgs; new evidence includes vLLM CVE-2026-41523 (malicious HF model → RCE) and DITTO pickle model scanner (0% FNR on 1,051-model benchmark).
- **New evidence on 2 existing trends**: PyCache Trap (bytecode cache attacks bypass 7 agent skill scanners at 94–100% ASR) added to agentic-injection-001; vLLM CVE-2026-41523 added to local-inference-001.
- **Rich arXiv haul**: 7 on-axis papers opened — BRANCH (100% guardrail bypass on 6 systems), NOMOS (NL policy → deterministic tool-call gates), LTBD (learnable prompt injection delimiters), Speedbumps (speculative decoding DoS), RAG security meta-model, and more.
- **Major tool releases**: llama.cpp b11516, Ollama v0.40.2 (cloud model proxy), promptfoo 0.124.1 (Claude Opus 5.5/GPT-6 support), transformers v5.19.0 (EmbeddingGemma2, expert parallelism), ExLlamaV3 v1.6.0 (AMD ROCm, CPU offloading).
- **Queue**: 2 resolved, +6 new → 13 live items.

## Trends

seed 0 · emerging 3 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-06-14](https://github.com/advisories/GHSA-q8gq-377p-jq3r) — vLLM CVE-2026-41523: malicious HF model → RCE via assert bypass |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-07](https://arxiv.org/abs/2610.10612) — PyCache Trap: bytecode cache substitution bypasses 7 agent skill scanners |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-07](https://arxiv.org/abs/2610.10735) — DITTO: context-aware pickle scanner, 0% FNR on 1,051-model benchmark |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11516 (2026-10-09); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched; CVE-2026-34159 RPC RCE (CVSS 9.8) fixed ≥b8492
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.2 (2026-10-08, model upgrade compat), v0.40.1 (2026-10-07, cloud API proxy); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, decision models, signed OCI galleries)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08): Claude Opus 5.5/Sonnet 5.5, GPT-6 Sol/Luna/6.1 Sol, Grok 4.7; 0.124.0 breaking: several SDKs/providers become opt-in
- **[transformers](https://github.com/huggingface/transformers)** — v5.19.0 (2026-10-06, EmbeddingGemma2, MoE router logits, expert parallelism)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.0 (2026-10-07): AMD ROCm support, faster CPU offloading, EXL3 quantization; consumer-GPU inference library (scope 1b)
- **[PyRIT](https://github.com/Azure/PyRIT)** — ARCHIVED (2026-03-27) — repository read-only, no releases; possible successors unverified

## Worth studying

- [PyCache Trap: The Inspection-Execution Gap in Agent Skill Scanners](https://arxiv.org/abs/2610.10612) — arXiv (2026-10-07): agent skill scanners miss malicious bytecode caches; 94–100% bypass across 7 scanners. Essential when vetting third-party agent skills/plugins.
- [NOMOS: Compiling Written Policies into Tool-Call Gates](https://arxiv.org/abs/2610.11030) — arXiv (2026-10-08): compiles NL policies into deterministic tool-call gates (zero ASR on AgentDojo banking); runs on-premise with gemma-4-26B.
- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): lifecycle hooks in agent harnesses are a blindspot — 92.5% compromise rate, 0% detection.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-09.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
