# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-11-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--10-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-10)

- **1 trend promoted seed→emerging**: [AI model & pipeline supply-chain attacks](#trends) now has 6 evidence items from ≥6 independent sources; SGLang CVE-2026-5760 (GGUF chat template → RCE, CVSS 9.8) and DITTO pickle scanner (9.3% of HF repos use unsafe pickle) added.
- **New evidence on all 3 trends**: SGLang CVE-2026-93034 (pickle deserialization CVSS 9.8) extends inference server attack surface; PyCache Trap (94–100% agent skill scanner bypass) expands agentic injection surface.
- **SGLang emerges as a major attack surface**: 29 GHSAs in 2026 alone (7 critical), spanning SSTI, pickle deserialization, and auth bypass.
- **8 new arXiv papers opened**: guardrail bypass (BRANCH, 100% ASR), policy-to-gate compiler (NOMOS, 0% ASR), speculative decoding DoS, LLM weight exfiltration detection, agent security incidents at OpenAI/Anthropic/Google.
- **ExLlamaV3 verified**: v1.6.0 (Oct 7) — EXL3 quantization, preliminary ROCm, CPU offload. Consumer GPU inference successor to ExLlamaV2.
- **PyRIT not dead**: development continued at microsoft/PyRIT (2231 commits, 48 open PRs).
- **Tool releases**: llama.cpp b11540, Ollama v0.40.2, promptfoo 0.124.1, transformers v5.19.0, ExLlamaV3 v1.6.0.

## Trends

seed 0 · emerging 3 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-08](https://github.com/advisories/GHSA-w4hv-c72g-pqx6) — SGLang CVE-2026-93034: pickle deserialization in IPC, CVSS 9.8 |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-07](https://arxiv.org/abs/2610.10612) — PyCache Trap: bytecode cache substitution bypasses 7 agent skill scanners 94–100% |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-07](https://arxiv.org/abs/2610.10735) — DITTO pickle scanner: 9.3% of top HF repos use unsafe pickle; 100% coverage, 0% FN |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11540 (2026-10-10); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.2 (2026-10-08, background model upgrades), v0.40.1 (2026-10-07); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, model failover chains)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.0 (2026-10-07): preliminary ROCm (gfx1100+), faster AVX2 CPU offload, EXL3 quantization. Consumer GPU inference; [TabbyAPI](https://github.com/theroyallab/tabbyAPI) = official server
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08): Claude 5.5, GPT-6 support; 0.124.0 breaking: hosted ChatKit removed, SDKs opt-in
- **[transformers](https://github.com/huggingface/transformers)** — v5.19.0 (2026-10-06, EmbeddingGemma2 multimodal, expert parallelism, per-layer cache config)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — active at microsoft/PyRIT (Azure/PyRIT archived 2026-03-27); absorbed into Microsoft Foundry AI Red Teaming Agent

## Worth studying

- [PyCache Trap: The Inspection-Execution Gap in Agent Skill Scanners](https://arxiv.org/abs/2610.10612) — arXiv (2026-10-07): agent skill scanners inspect source but Python runs bundled bytecode caches; 94–100% bypass rate across 7 scanners. Directly relevant when vetting third-party agent plugins/skills.
- [ExLlamaV3 v1.6.0](https://github.com/turboderp-org/exllamav3/releases/tag/v1.6.0) — turboderp-org (2026-10-07): consumer-GPU inference with EXL3 quantization (QTIP-based), preliminary ROCm support, tensor/expert parallelism, CPU offload. RTX 4070 Ti relevant.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-10.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
