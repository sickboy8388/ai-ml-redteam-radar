# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-11-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--15-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-15, daily)

- **local-inference-001** (accelerating, held): vLLM discloses 7 new GHSAs Nov 13-15 (3 High incl. CVSS 8.7 processor-kwargs DoS); W46 demotion caveat cleared. llama.cpp b12403, Ollama v0.40.16, transformers v5.22.2 (Jinja sandbox hardening).
- **agentic-injection-001** (accelerating, held): arXiv Nov 13 carries 7+ on-axis papers — abstention manipulation as availability attack (86.3% induced over-abstention), OverServe 93.88× resource amplification, SideTaskBench 40% unauthorized delivery, CapLite PI defense for small LMs, PolicySniff GPU side-channel.
- **ai-supplychain-001** (emerging, held): QHijack-LoRA — malicious adapter passes full-precision audit, activates under quantization. Lazarus — <10 edited neurons create sleeper agents (98.8%+ trigger rate). transformers Jinja hardening.
- **llm-frontend-001** (seed, held): 1 new Langflow advisory (High, Nov 8).
- **agentic-offensive-ops-001** (seed, held): no new campaign primary from a second org; Wiz Cyber Model Arena and Sysdig "Under the hood" opened as context.
- **Queue**: 11 live; Gheist/GhostAction dropped (W46 deadline). **Study shelf**: +2 (PyRIT v1.2.0, QHijack-LoRA).

## Trends

seed 2 · emerging 1 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-13](https://github.com/advisories/GHSA-h8w4-vgpr-474w) — vLLM 7-advisory batch: CVE-2026-126397 (High, CVSS 8.7) request-controlled processor kwargs → quadratic CPU DoS |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-13](https://arxiv.org/abs/2611.14864) — Abstention manipulation: fabricated risk warnings induce 86.3% over-abstention in tool-using agents |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-11-11](https://arxiv.org/abs/2611.14978) — QHijack-LoRA: malicious adapter passes full-precision audit, activates under quantization |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | seed | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow OSS CVE-2026-97677 (High): attacker-controlled data write via authenticated flow |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns](TRENDS.md#trends) | seed | [2026-10-30](https://www.wiz.io/blog/black-october-for-ai-developer-platforms) — Wiz: "Black October" — 9+ AI dev platforms breached; LLMjacking at scale |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12403 (2026-11-15); Vulkan FA optimizations, cooperative softmax, sycl improvements; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.16 (2026-11-09, Qwen3.8 Flash Next memory savings, Ripple Preview, CUDA 13.5 ARM); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02); 7 new GHSAs Nov 13-15 (3 High, all fixed <0.31.0); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.23.0 (2026-11-13, Inkling2 594B MoE, LFM3-VL, Dots 3 Note); v5.22.2 (Nov 6, hardened Jinja sandboxing)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.0 (2026-11-13); CoPyRIT GUI, GOAT/jailbreak/A2A attacks, GitHub Copilot target, ASSERT scoring
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): pipelined prefill, split-device quantization fixes; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.917-beta (2026-11-11): Qwen3.8-27B Dynamic GGUFs, Claude Code/Codex on MLX, metadata host blocking hardening; RTX 4070 Ti relevant

## Worth studying

- [PyRIT v1.2.0](https://github.com/microsoft/PyRIT/releases) — Microsoft (2026-11-13): major red-team tool release — CoPyRIT GUI, GOAT/jailbreak techniques, GitHub Copilot target, ASSERT scoring. The primary open-source AI red-team framework now has a full GUI and expanded attack surface coverage.
- [QHijack-LoRA: Hijacking Trusted LLMs via Disguised Adapters in Quantized Deployments](https://arxiv.org/abs/2611.14978) — arXiv (2026-11-11): malicious adapter passes audit, activates under quantization. Must-know for anyone deploying quantized local models with third-party adapters.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): 12 local configs (4B–27B) on CyberGym vuln-reproduction tasks; quantization doesn't change solvability, MoE faster. Directly relevant for red-teaming with consumer GPUs.
- [KVGuard: A KV Cache Safety Checker for LLM Serving Systems](https://arxiv.org/abs/2611.06138) — arXiv (2026-11-04): finds KV-cache memory-safety bugs in vLLM/SGLang; 8 previously unknown violations at 3–7.4% overhead.
- [Sysdig: three layers of open source defense for AI coding agents](https://www.sysdig.com/blog/three-layers-of-open-source-defense-for-ai-coding-agents-openshell-prempti-and-falco) — Sysdig (2026-10-27): OpenShell + Prempti + Falco layered defense blueprint for securing AI coding agents.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-15.md) · [Latest weekly](reports/weekly/2026-W45.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
