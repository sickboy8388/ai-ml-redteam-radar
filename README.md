# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-8-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--14-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-14, daily)

- **local-inference-001** (accelerating, held): llama.cpp **v1.0.0** ships multiple security fixes (DNS rebinding, CORS proxy SSRF, child instance access, HF_TOKEN leak, unauthenticated tools default-off); LMDeploy CVE-2026-123818 (CVSS 7.5 SSRF, 3rd CVE this quarter); vLLM 6 new GHSAs Nov 13 (3 High incl. CVSS 8.7). W46 demotion caveat cleared.
- **agentic-injection-001** (accelerating, held): ~20 arXiv papers Nov 10-14 — "Agents of Chaos" SoK (284 attacks), second impossibility theorem for gatekeeping, Lazarus dormant-neuron backdoor (98.8%), ShadowBench-MCP (29.2% shadow invocations), ActiveSecHarness (ABR=1.000). Paper velocity ≥20/week.
- **ai-supplychain-001** (emerging, held): QHijack-LoRA adapter attack on quantized deployments + StealthyPoison procedural skill poisoning; dormancy averted. No second package compromise yet.
- **llm-frontend-001** (seed, held): 1 new Langflow path-traversal advisory (CVSS 8.1). No new project joined.
- **agentic-offensive-ops-001** (seed, held): no new second-org primary; dormancy at 15 days.
- **Queue**: 8 live; Gheist/GhostAction dropped; arXiv Nov 3-4 gap resolved.

## Trends

seed 2 · emerging 1 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-13](https://github.com/ggml-org/llama.cpp/releases/tag/v1.0.0) — llama.cpp v1.0.0 security hardening + LMDeploy SSRF (7.5) + vLLM 6 GHSAs (3 High) |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-13](https://arxiv.org/abs/2611.15118) — Lazarus: <10 neuron edits backdoor AI agents at 98.8% trigger success; SoK catalogues 284 atomic attacks |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-11-11](https://arxiv.org/abs/2611.14978) — QHijack-LoRA: adapter hijacks quantized deployments; StealthyPoison: procedural skill poisoning evades detectors |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | seed | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow OSS path traversal (CVSS 8.1) + prior 25 GHSAs incl. 6 Critical |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns](TRENDS.md#trends) | seed | [2026-10-30](https://www.wiz.io/blog/black-october-for-ai-developer-platforms) — Wiz: "Black October" — 9+ AI dev platforms breached; LLMjacking at scale |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — **v1.0.0** (2026-11-13); security: DNS rebinding fix, CORS proxy SSRF fix, child instance access blocked, HF_TOKEN restricted, unauthenticated tools require opt-in; FP8 KV caches; breaking API changes (35 deprecated fns removed, clip.h consolidated). Security floor: ≥v1.0.0
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.16 (2026-11-09, Latest); v0.40.17-rc0 (Nov 10); no security fixes; security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02); 6 new GHSAs Nov 13 (3 High, all fixed ≤0.31.0); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.1 (2026-10-30, Mistral Large 4 ~1T MoE, FP8 adapter training via PEFT)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): split-device quant fixes, pipelined prefill; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.917-beta (2026-11-11): Qwen3.8-27B Dynamic v3.1 GGUFs, FLUX VRAM reduction, INT8/FP8 on older NVIDIA cards, 2-8x faster generate on T4; RTX 4070 Ti relevant

## Worth studying

- [QHijack-LoRA: Hijacking Quantized LLM Deployments via Disguised Adapters](https://arxiv.org/abs/2611.14978) — arXiv (2026-11-11): adapter-only attack dormant at full precision, activates on quantized base; crosses the audit gap between test and deploy. Essential for anyone pulling LoRA adapters for local quantized deployments.
- [llama.cpp v1.0.0](https://github.com/ggml-org/llama.cpp/releases/tag/v1.0.0) — ggml-org (2026-11-13): milestone security hardening release. Essential update for anyone running llama-server.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): 12 local configs (4B–27B) on CyberGym vuln-reproduction tasks; quantization doesn't change solvability, MoE faster. Directly relevant for red-teaming with consumer GPUs.
- [KVGuard: A KV Cache Safety Checker for LLM Serving Systems](https://arxiv.org/abs/2611.06138) — arXiv (2026-11-04): finds KV-cache memory-safety bugs in vLLM/SGLang; 8 previously unknown violations at 3–7.4% overhead.
- [Sysdig: three layers of open source defense for AI coding agents](https://www.sysdig.com/blog/three-layers-of-open-source-defense-for-ai-coding-agents-openshell-prempti-and-falco) — Sysdig (2026-10-27): OpenShell + Prempti + Falco layered defense blueprint for securing AI coding agents.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
- [NameTrap: Steering AI Coding Agents Toward Security Vulnerabilities via Variable Names](https://arxiv.org/abs/2610.34253) — arXiv (2026-10-25): poisoned identifier names steer 6 coding agents toward CWE weaknesses (22–56% ASR); practical threat for anyone using AI assistants with untrusted repos.
- [SCS: Supply-Chain Scanner for Agent Skills](https://arxiv.org/abs/2610.33489) — arXiv (2026-10-24): program analysis finds 627 confirmed malicious skills in 66k ClawHub skills. First large-scale automated detection.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-14.md) · [Latest weekly](reports/weekly/2026-W45.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
