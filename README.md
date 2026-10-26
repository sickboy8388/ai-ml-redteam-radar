# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-8-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--07-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-07)

- **2 trends promoted emerging→accelerating**: [Self-hosted inference server attack surface](#trends) now has 9 evidence items from ≥7 independent orgs including in-the-wild exploitation and a new vLLM CVE (assert-bypass → RCE via malicious HF model); [Agentic prompt-injection & agent-subsystem attacks](#trends) now has 10 evidence items — SkillPoison achieves 95.71% attack success through valid trajectories, and HarnessSecurity-Bench shows auto-approval raises attack success from 29.2% to 95.6% across 6 coding-agent harnesses.
- **ai-supplychain-001 grows**: +1 evidence (vLLM CVE-2026-41523 cross-reference — malicious HuggingFace model triggers code execution).
- **6 observation_queue items resolved**: PyRIT not archived (corrected — active at microsoft/PyRIT v1.1.0), ExLlamaV3 verified (v1.5.4), Ollama v0.40.0 MLX confirmed, Unsloth MoE verified, OWASP GenAI LLM Top 10 2026 verified, vLLM CVE routed.
- **Tool releases**: promptfoo 0.124.0 (Oct 6), ExLlamaV3 v1.5.4 (Oct 3), PyRIT v1.1.0 (Sep 4).
- **Promptfoo acquired by OpenAI** (Mar 2026) — major red-team tooling landscape shift.
- **Queue**: +6 new items, 6 resolved → 8 live items.

## Trends

seed 1 · emerging 0 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-07](https://github.com/advisories/GHSA-q8gq-377p-jq3r) — vLLM CVE-2026-41523: malicious HF model → RCE via assert bypass in optimized mode |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-06](https://arxiv.org/abs/2610.07639) — HarnessSecurity-Bench: auto-approval → 95.6% attack success across 6 coding-agent harnesses |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-07](https://github.com/advisories/GHSA-q8gq-377p-jq3r) — vLLM CVE-2026-41523: malicious HuggingFace model exploits assert-based validation → RCE |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11461 (2026-10-07); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.0 (2026-09-25, MLX default on Apple Silicon, decision models), v0.35.1 (2026-09-29, Clef /v1/systemone API); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, model failover chains, Sigstore-signed OCI galleries)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.0 (2026-10-06): Claude Opus 5.5/Sonnet 5.5, GPT-6 variants; note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.18.0 (2026-09-30, Nemotron 3 Diarization, HyperCLOVAX Vision V2, GTE)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04): Best-of-N/multilingual/audio attacks, 488 TrustAIRLab jailbreak templates, GUI scenario catalog; note: active at microsoft/PyRIT (Azure/PyRIT is an archived stub)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.5.4 (2026-10-03): EXL3 quantization (QTIP-based), token-embedding quantization, CPU MoE offload, speculative decoding; 1.6K stars
- **[Unsloth](https://unsloth.ai)** — 2026 MoE update: 12x faster MoE fine-tuning, 35%+ less VRAM; gpt-oss-20b on 12.8GB VRAM; supports Qwen3/DeepSeek/GLM

## Worth studying

- [ExLlamaV3 v1.5.4](https://github.com/turboderp-org/exllamav3/releases) — turboderp-org (2026-10-03): consumer-GPU inference with EXL3 quantization, speculative decoding, CPU MoE offload. Directly relevant to the 1b stack for RTX 4070 Ti builds.
- [OWASP GenAI LLM Top 10 2026](https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/) — OWASP (2026-08-03): first incident-weighted LLM risk taxonomy (6,639 real incidents); Excessive Agency → LLM03, Hidden Context Exposure replaces System Prompt Leakage. Baseline for red-team scoping.
- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): lifecycle hooks in agent harnesses are a blindspot — 92.5% compromise rate, 0% detection. Assess local agent setups with plugin/hook systems.
- [Unsloth 2026 MoE Update](https://unslothai.substack.com/p/unsloth-2026-update-faster-moe) — Unsloth (2026-02-10): 12x faster MoE fine-tuning with 35%+ less VRAM; gpt-oss-20b fits 12.8GB. Relevant for RTX 4070 Ti QLoRA workflows.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): systematic audit of llama.cpp; 5 of 10 bugs unpatched.

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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-07.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
