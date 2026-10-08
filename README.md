# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-1-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-6-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--08-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-08)

- **Agentic injection → accelerating**: arXiv burst (Oct 6-8) adds 5+ independent groups spanning rule-file injection for coding agents (PackHallu), adversarial visual hijacking of web agents (91.9% success, WebMirage), automated red-teaming engines (ASPIRE), credential-leakage benchmarks, and formal runtime verification. Promoted emerging→accelerating.
- **New evidence**: vLLM CVE-2026-54234 (DoS via speculative decoding, CVSS 7.5) added to inference-server trend; vLLM CVE-2026-41523 (code execution via malicious HuggingFace model) verified and added to supply-chain trend.
- **Queue resolved**: 6 items verified and closed — vLLM CVE-2026-41523 (→ supply-chain evidence), PyRIT (not dead: moved to microsoft/PyRIT v1.1.0), ExLlamaV3 (active, v1.6.0), Ollama MLX (→ v0.40.1 stable), Unsloth MoE (verified), OWASP GenAI LLM Top 10 2026 (verified Aug 3 v1.0).
- **Tool releases**: llama.cpp b11491, Ollama v0.40.1 stable, ExLlamaV3 v1.6.0 (ROCm), promptfoo 0.124.0, transformers v5.19.0, PyRIT v1.1.0.

## Trends

seed 1 · emerging 1 · accelerating 1 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks, rule files, visual grounding)](TRENDS.md#trends) | accelerating | [2026-10-07](https://arxiv.org/abs/2610.09264) — PackHallu: rule-file injection makes coding agents install attacker-controlled packages |
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-08](https://github.com/advisories/GHSA-8wr5-jm2h-8r4f) — vLLM CVE-2026-54234: remote DoS via speculative decoding, CVSS 7.5 |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-08](https://github.com/advisories/GHSA-q8gq-377p-jq3r) — vLLM CVE-2026-41523: malicious HF model → code execution via assert bypass |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11491 (2026-10-08); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.1 stable (2026-10-07, cloud usage APIs, Windows fixes); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05); security floor: ≥0.24.0 (CVE-2026-54234 DoS + CVE-2026-55514), ≥0.22.0 (CVE-2026-41523 RCE), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes); v4.10.0 (2026-09-17, fleet ops dashboard)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.0 (2026-10-07): ROCm support, faster CPU offloading, EXL3 quantization; consumer-GPU optimized (under 16GB for 3bpw + 4096-token cache)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.0 (2026-10-06): newer Claude/GPT-6/Grok models; breaking: provider SDKs now opt-in
- **[transformers](https://github.com/huggingface/transformers)** — v5.19.0 (2026-10-06, EmbeddingGemma2, expert-parallelism, per-layer cache config)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04): improved scoring, scanner expansion, GUI scenario catalog; v1.0.0 GA (Jul 24)
- **[Unsloth](https://github.com/unslothai/unsloth)** — MoE training 12x faster, 35% less VRAM; gpt-oss-20b fits 12.8GB VRAM (scope 1b: consumer-GPU fine-tuning)

## Worth studying

- [PackHallu: Package Hallucination Attacks on Coding Agents through Rule File Injection](https://arxiv.org/abs/2610.09264) — arXiv (2026-10-07): prompt injection in .cursorrules / AGENTS.md makes coding agents install attacker-controlled packages. Directly relevant to anyone using AI coding assistants with community-shared rule files.
- [ASPIRE: Agentic Safety & Prompt Injection Red-teaming Engine](https://arxiv.org/abs/2610.08951) — arXiv (2026-10-06): automated red-teaming engine for discovering indirect prompt-injection risks in tool-using LLM agents.
- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): lifecycle hooks in agent harnesses are a blindspot — 92.5% compromise rate, 0% detection.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): systematic audit of llama.cpp; 5 of 10 bugs unpatched.
- [InjecMEM: Memory Injection Attack on LLM Agent Memory Systems](https://arxiv.org/abs/2608.23471) — arXiv (2026-08-24): agent memory is a demonstrated injection target.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-08.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
