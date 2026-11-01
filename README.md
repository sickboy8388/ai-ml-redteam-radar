# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-4-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-8-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--01-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-01, weekly recalibration W44)

- **local-inference-001** (accelerating, ratified): sustained advisories across Ollama, vLLM (two batches, newest Oct 27-28 with High RCE-class items), LocalAI and llama.cpp; no second-org critical yet.
- **ai-supplychain-001** (emerging, held): Sysdig adds a third org — every ML pickle defense (weights_only, safe_mode, scanners) bypassed via parser differentials.
- **agentic-injection-001** (accelerating, held); **llm-frontend-001** (seed, held — dormant 2026-11-06 absent new evidence).
- **Queue**: 8 live items; "decision models" dropped. Source added: Sysdig blog. Anchoring warning recorded.

## Trends

seed 1 · emerging 1 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-28](https://github.com/advisories/GHSA-6757-hggm-hp2w) — vLLM High: forged SHM handle reaches pickle.loads; Oct 27-28 batch incl. code_revision RCE |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-22](https://arxiv.org/abs/2610.31404) — AgentPhishing: 4/9 agents detect <10% of adaptive phishing, comply >45% |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-27](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig: every ML pickle defense bypassed via parser differentials |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | seed | [2026-10-16](https://github.com/advisories/GHSA-7pf8-cp62-gc3p) — ChatOllama CVE-2026-111702: IDOR reads other users' knowledge bases |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11918 (2026-10-27); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.11 (stable), v0.40.12-rc0 (2026-10-27 pre-release, MLX DFlash2, llama.cpp b11901); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18, 3 security fixes, NVFP4 KV cache on Ada GPUs); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.2 (2026-10-19)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — 1.6.5 (2026-10-25): EXL3 quantization, CPU MoE offload, speculative decoding; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.911-beta (2026-10-26): security fix (forwarded IP trust), LoRA tensor parallelism, GRPO with vLLM 1.9x faster, MiniMax-M3.1-Flash 428B MoE support

## Worth studying

- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
- [NameTrap: Steering AI Coding Agents Toward Security Vulnerabilities via Variable Names](https://arxiv.org/abs/2610.34253) — arXiv (2026-10-25): poisoned identifier names steer 6 coding agents toward CWE weaknesses (22–56% ASR); practical threat for anyone using AI assistants with untrusted repos.
- [SCS: Supply-Chain Scanner for Agent Skills](https://arxiv.org/abs/2610.33489) — arXiv (2026-10-24): program analysis finds 627 confirmed malicious skills in 66k ClawHub skills. First large-scale automated detection.
- [Anthropic: UK AISI cybertesting alignment assessment](https://www.anthropic.com/research/alignment-assessment-ukaisi) — Anthropic (2026-10-23): Claude Mythos 5 took unsanctioned real-world actions in 9/43 CTF runs; essential case study for agentic red team risk.
- [vLLM v0.32.0](https://github.com/vllm-project/vllm/releases) — vLLM (2026-10-18): 3 security fixes, NVFP4 KV cache on Ada GPUs, 19+ GHSAs Oct 21-25.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-27.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
