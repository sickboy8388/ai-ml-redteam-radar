# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-9-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--17-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-17)

- **Agentic attacks keep growing**: two new attack classes — APEX skill-chaining (74.2% ASR) and LLMLeak covert exfiltration via web-fetching (79.7% ASR) — fill the last evidence slots on the agentic-injection trend.
- **vLLM launches systematic security advisory program**: 5 new advisories on Oct 6 including RCE via request-controlled `code_revision`; fourth batch in five weeks. Added to inference-server trend (now 10/10 evidence).
- **Supply-chain trend goes dormant**: 62 days without new multi-org evidence; reactivates on fresh signal.
- **Ollama SSRF disclosed**: CVE-2026-108836 in Pull API (Moderate, fixed 0.34.2) — queued as evidence overflow.
- **ExLlamaV3 rapid development**: v1.5.0→v1.6.2 in 5 weeks — ROCm support, hybrid drafting, faster CPU offload for consumer GPUs.
- **Study picks**: Unsloth 2026 MoE update (12x fine-tuning speedup, QLoRA on consumer GPUs); PACE agent defense framework (0/30 adaptive attacks).

## Trends

seed 0 · emerging 2 · accelerating 0 · mainstreaming 0 · dormant 1

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-06](https://github.com/vllm-project/vllm/security/advisories) — vLLM Oct advisory batch: 5 advisories incl. RCE via code_revision (High) |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-02](https://arxiv.org/abs/2610.03448) — PI detector re-evaluation: benchmark scores mislead deployment |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | dormant | [2026-08-16](https://arxiv.org/abs/2608.15913) — 62 days without new evidence; reactivate on fresh signal |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11706 (2026-10-17); Beam model support (b11701), proxy env var fix (b11699); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.5 Latest (2026-10-14, decision models on cloud), v0.40.6 pre-release (2026-10-16); security floor: ≥0.34.2 (CVE-2026-108836 SSRF), ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security advisory program active (4 batches since Sep 3); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, decision models, signed OCI galleries)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16): hit@k ASR metric, Python 3.14 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08): cost recording, OpenAI Decisions support; 0.124.0 breaking (SDKs opt-in)
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.1 (2026-10-16, Beam model); v5.20.0 (Oct 15, Muse Spark Open, Ling 3.0, UltraBERT, quantized export)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); Azure/PyRIT archived 2026-03-27 (moved here)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.2 (2026-10-14): ROCm support (v1.6.0), hybrid drafting, faster CPU offload; very active (v1.5.0→v1.6.2 in 5 weeks); fits 12GB RTX 4070 Ti

## Worth studying

- [Unsloth 2026 Update — Faster MoE](https://unslothai.substack.com/p/unsloth-2026-update-faster-moe) — Unsloth (2026-02-10): 12x MoE training speedup, QLoRA on consumer GPUs (gpt-oss-20b in 12.8GB VRAM), 500+ models; the practical fine-tuning framework for consumer hardware.
- [PACE: Provenance-Aware Capability Enforcement](https://arxiv.org/abs/2610.01349) — arXiv (2026-10-01): mediates every tool call pre-execution; lowest ASR in 62/79 attack columns; 0/30 adaptive attacks. Strongest defensive framework for tool-using agents.
- [ExLlamaV3](https://github.com/turboderp-org/exllamav3) — turboderp-org (accessed 2026-10-17): v1.6.2 with ROCm support, hybrid drafting, faster CPU offload; EXL3 quantization for consumer GPUs.
- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): 92.5% compromise rate across 7 harnesses, 0% detection. Assess local agent setups.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): 5 of 10 bugs unpatched. Essential for anyone running llama.cpp.

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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-17.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
