# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-14-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--06-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-06)

- **`ai-supplychain-001` promoted seed→emerging**: vLLM CVE-2026-41523 (assert bypass → RCE via malicious HuggingFace model) verified and added as 5th independent source; now 5 evidence items from 5 orgs.
- **`agentic-injection-001` evidence filled (10/10)**: Runaway Reaction (CRIME framework: benign agent skills compose into malicious behavior, 4,000 skills evaluated) + Exposed by Design (414 internet-facing MCP servers assessed: 91% lack OAuth, 687 shell-exec tools, 68 reportable vulns).
- **llama.cpp v0.6.0**: major release — extended batch API (`llama_batch_ext`), GLM-5.3-Flash 320B, Clef decision models, Metal tensor-API flash attention, ggml v0.26.0.
- **promptfoo 0.124.0**: Claude Opus 5.5/Sonnet 5.5 support, GPT-6 models, optional SDK breakout.
- **Queue**: +6 new items (SGLang SafeUnpickler bypass, LiteLLM 6 CVEs CVSS 10.0 chain, GitLab AI Gateway CVSS 9.9, provider-side IPI, RAISED defense, watermarking hallucination), 2 resolved → 14 live items.
- **Study picks**: ExLlamaV3 v1.5.3 (consumer GPU inference, EXL3 quantization); Runaway Reaction (skill composition attacks).

## Trends

seed 0 · emerging 3 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-05](https://www.stingrai.io/blog/inference-server-security-vllm-triton-ollama-2026) — CVE roundup: Triton auth bypass 9.8, vLLM RCE 9.8, llama.cpp UAFs |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | emerging | [2026-10-05](https://arxiv.org/abs/2610.05943) — Runaway Reaction: benign skills compose into malicious behaviors via CRIME framework |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-08-16](https://arxiv.org/abs/2608.15913) — Conjunctive Poisoning: deployment artifacts alter model behavior without weight modification |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — v0.6.0 (2026-10-05, extended batch API, GLM-5.3-Flash, Clef, ggml v0.26.0), b11435 (2026-10-06); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.35.1 (2026-09-29, Clef decision models), v0.40.0-rc3 (2026-09-25, MLX runtime pre-release); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, DeepSeek-V4.1-Flash, persistent weight caching); security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, model failover chains, decision models)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Ollama generator improvements, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.0 (2026-10-06): Claude Opus 5.5/Sonnet 5.5, GPT-6, optional SDK breakout
- **[transformers](https://github.com/huggingface/transformers)** — v5.18.0 (2026-09-30, Nemotron 3 Diarization, HyperCLOVAX Vision V2, GTE)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.5.3 (2026-09-27): EXL3 quantization (2–8 bit), tensor/expert-parallel, CPU offload, 50+ model architectures; TabbyAPI backend
- **[Unsloth](https://github.com/unslothai/unsloth)** — 12x MoE speedup, gpt-oss-20b fine-tunes in 12.8GB VRAM; joined PyTorch ecosystem (May 2026); QLoRA not yet supported for MoE
- **[PyRIT](https://github.com/Azure/PyRIT)** — ARCHIVED (2026-03-27) — repository read-only, no releases

## Worth studying

- [ExLlamaV3: optimized quantization & inference for consumer GPUs](https://github.com/turboderp-org/exllamav3) — turboderp-org (v1.5.3, 2026-09-27): EXL3 quantization, tensor/expert-parallel, CPU offload, 50+ model architectures. Essential for RTX 4070 Ti operators.
- [Runaway Reaction: When Benign Skills Compose into Malicious Behavior](https://arxiv.org/abs/2610.05943) — arXiv (2026-10-05): CRIME framework shows individually vetted agent skills combine into harmful emergent behaviors. Must-read for multi-skill agent deployments.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-06.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
