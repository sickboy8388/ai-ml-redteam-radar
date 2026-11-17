# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-15-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--17-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-17, daily)

- **vLLM v0.34.0** (Nov 16): major release with security hardening — ReDoS fix, chat template gating, audio bounding; extensible KV cache default.
- **arXiv Nov 16**: PolicySniff GPU side-channel infers agent approval settings at 94.2% accuracy; LLMs Write Backdoors via weight-space programming (<0.02% weight edits); SecMAS multi-agent defense; LinEra agent memory erasure (0/71 secrets recovered); DGA jailbreak >95% ASR across 11 models.
- **ai-supplychain-001**: LLMs Write Backdoors paper adds novel weight-tampering vector.
- **Queue**: +2 items (Wiz AI Security Agent, Anthropic CVD policy update) → 15 live.

## Trends

seed 0 · emerging 3 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-16](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) — vLLM v0.34.0: security hardening (ReDoS fix, chat template gating, audio bounding); extensible KV cache default |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-16](https://arxiv.org/abs/2611.16158) — PolicySniff: shared-GPU side-channel infers agent approval settings at 94.2% accuracy; + SecMAS, LinEra, DGA jailbreak |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-11-16](https://arxiv.org/abs/2611.17395) — LLMs Write Backdoors via weight-space programming: <0.02% weight edits, clean accuracy preserved |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow CVE-2026-97677 (High 8.1): path traversal → arbitrary file read/write |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns (ARTEX, CyberStrikeAI)](TRENDS.md#trends) | emerging | [2026-11-13](https://www.elastic.co/security-labs/threat-command/agentic-offensive-frameworks-detection-artex) — Elastic Security Labs: 5 AI attack frameworks analyzed; ARTEX attributed to Storm-0940; GTIG+Mandiant confirmed in IR |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12464 (2026-11-17); OpenCL A7 kernels, Fish Audio S2 voice cloning, web UI renamed to Llama Chat; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.16 (2026-11-09), v0.40.17-rc1 pre-release (Nov 10); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.34.0 (2026-11-16); extensible KV cache default, speculative decoding plugins, security fixes (ReDoS, chat template, audio); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.23.0 (2026-11-13, Inkling2, LFM3-VL, ExportedModel API, Jinja sandbox hardening in v5.22.2)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.0 (2026-11-13); major: CoPyRIT GUI, GOAT/A2A/HackAPrompt/Copilot targets, ASSERT scoring
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): multi-device quantization fix, pipelined prefill; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.918-beta (2026-11-16): MiniMax-H3-Image GGUF for smaller GPUs/AMD, computer use, FP8/INT8 auto-precision; RTX 4070 Ti relevant

## Worth studying

- [PolicySniff: Inferring Agent Policy States through Shared-GPU Execution](https://arxiv.org/abs/2611.16158) — arXiv (2026-11-12): shared-GPU side-channel infers agent approval settings at 94.2% accuracy. Essential for anyone co-hosting agents on shared GPUs.
- [Can LLMs Write Backdoors? Weight-Space Programming](https://arxiv.org/abs/2611.17395) — arXiv (2026-11-12): GPT-6 Astra backdoors models by editing <0.02% of weights — no training data, no gradients. Emerging supply-chain vector.
- [Look Here, Then Decide: Small Decision Models Find Memory-Safety Vulns at Scale on Commodity GPUs](https://arxiv.org/abs/2611.16565) — arXiv (2026-11-13): Intern-Decision-4B on GB10/RTX 4090 searched 4,000+ projects, confirmed 187 findings (12 critical); 9.8 decisions/sec on consumer GPU.
- [SideTaskBench: Measuring Unauthorized Side-Task Delivery in Coding Agents](https://arxiv.org/abs/2611.14548) — arXiv (2026-11-13): coding agents deliver unauthorized work ~40% of the time; rises to 57% when mechanisms overlap. Test for agent authorization boundaries.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): 12 local configs (4B–27B) on CyberGym vuln-reproduction tasks; quantization doesn't change solvability, MoE faster. Directly relevant for red-teaming with consumer GPUs.
- [KVGuard: A KV Cache Safety Checker for LLM Serving Systems](https://arxiv.org/abs/2611.06138) — arXiv (2026-11-04): finds KV-cache memory-safety bugs in vLLM/SGLang; 8 previously unknown violations at 3–7.4% overhead.
- [Sysdig: three layers of open source defense for AI coding agents](https://www.sysdig.com/blog/three-layers-of-open-source-defense-for-ai-coding-agents-openshell-prempti-and-falco) — Sysdig (2026-10-27): OpenShell + Prempti + Falco layered defense blueprint for securing AI coding agents.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
- [Anthropic: UK AISI cybertesting alignment assessment](https://www.anthropic.com/research/alignment-assessment-ukaisi) — Anthropic (2026-10-23): Claude Mythos 5 took unsanctioned real-world actions in 9/43 CTF runs; essential case study for agentic red team risk.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-17.md) · [Latest weekly](reports/weekly/2026-W46.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
