# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-6-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--12-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-12, daily)

- **local-inference-001** (accelerating, held): new LMDeploy CVE-2026-123818 (CVSS 7.5, SSRF via URL parser differential); 3rd LMDeploy flaw. W45 demotion caveat cleared. llama.cpp b12317 (Nov 12, b12307 Metal OOB read fix).
- **agentic-injection-001** (accelerating, held): arXiv Nov 11 carries 7+ on-axis papers — ActiveSecHarness neurosymbolic monitor for coding harnesses, second impossibility theorem for agent gatekeeping. Paper velocity sustained.
- **llm-frontend-001** (seed, held): new Langflow CVE-2026-97677 (CVSS 8.1, path traversal read/write); dormancy clock reset.
- **ai-supplychain-001** (emerging, held), **agentic-offensive-ops-001** (seed, held): no new evidence.
- **Queue**: 6 live; Gheist/GhostAction dropped (W46 deadline). Study shelf +2 (BypassGym EDR evasion benchmark, RAG geometric access control).

## Trends

seed 2 · emerging 1 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-09](https://github.com/advisories/GHSA-39wr-7q6h-cf68) — LMDeploy CVE-2026-123818 SSRF via URL parser differential (CVSS 7.5); 3rd LMDeploy flaw |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-11](https://arxiv.org/abs/2611.13960) — ActiveSecHarness: neurosymbolic reference monitor for agentic coding harnesses; ABR 1.0/FPR 0.0 at ~13µs |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-27](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig: every ML pickle defense bypassed via parser differentials |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | seed | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow OSS CVE-2026-97677 (CVSS 8.1): path traversal read/write; 26+ Langflow advisories total |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns](TRENDS.md#trends) | seed | [2026-10-30](https://www.wiz.io/blog/black-october-for-ai-developer-platforms) — Wiz: "Black October" — 9+ AI dev platforms breached; LLMjacking at scale |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12317 (2026-11-12); b12307 Metal OOB read fix (SOLVE_TRI kernel); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.16 (2026-11-09, reduced memory Qwen3.8 Flash Apple Silicon, CUDA 13.5 ARM); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25)
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.2 (2026-11-06, security: Jinja sandboxing hardened)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.6 (2026-10-31): greatly reduced VRAM during quantization, DeepseekV41 + Lfm3 support; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.917-beta (2026-11-11): 2–8x faster generate() on T4/consumer GPUs, FP8 LoRA training, .safetensors-only NVFP4 loading (pickle hardening); RTX 4070 Ti relevant

## Worth studying

- [BypassGym: A Benchmark for Evaluating AI Agents' Endpoint Defense Evasion Capabilities](https://arxiv.org/abs/2611.13684) — arXiv (2026-11-10): first benchmark testing AI agent EDR evasion on real Windows endpoints; DeepSeek-V4.1 Flash 17/18 runs. Essential baseline for agent offensive capability assessment.
- [Isolation Is Not Confidentiality: Security Boundaries of Geometric Access Control in RAG](https://arxiv.org/abs/2611.14061) — arXiv (2026-11-10): geometric access control prevents cross-policy retrieval but not embedding recovery, query forgery, or membership leakage.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-12.md) · [Latest weekly](reports/weekly/2026-W45.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
