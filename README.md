# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-9-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--09-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-09, daily)

- **agentic-injection-001** (accelerating, held): arXiv Nov 9 listing carries ≥13 on-axis papers — Thought Injection (50% ASR on reasoning agents via thought-trace PI), Authorization Drift (0.43–0.61 drift rates without adversary), MemoryDojo (all 5 memory systems susceptible). Three evidence swaps. Paper velocity now ≥13/day.
- **local-inference-001** (accelerating, held): llama.cpp b12211 (Nov 8, no security fixes). NVD sweeps: 0 new CVEs since Oct 30 (10 days quiet). W46 demotion caveat stands.
- **ai-supplychain-001** (emerging, held), **llm-frontend-001** (seed, held; 11 days since Langflow batch), **agentic-offensive-ops-001** (seed, held; Microsoft blog still 404).
- **Queue**: 9 live (added Sysdig enterprise agent observability, 2 MCP security tools). **Study shelf**: +2 (Aegis OS runtime, Thought Injection).

## Trends

seed 2 · emerging 1 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-30](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-119706) — NVD: LMDeploy unauth pickle RCE (CVSS 9.3) + LM Studio path traversal (8.7); 10 days quiet |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-09](https://arxiv.org/abs/2611.08811) — Thought Injection: thought-trace PI reaches 50% ASR on reasoning agents vs 0% for standard PI |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-27](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig: every ML pickle defense bypassed via parser differentials |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | seed | [2026-10-29](https://github.com/advisories/GHSA-mm82-q33r-3rjw) — IBM Langflow OSS: 25 GHSAs incl. 6 Critical (CVSS 9.8) RCE/auth-bypass |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns](TRENDS.md#trends) | seed | [2026-10-30](https://www.wiz.io/blog/black-october-for-ai-developer-platforms) — Wiz: "Black October" — 9+ AI dev platforms breached; LLMjacking at scale |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12211 (2026-11-08); MoE cache, radix Top-K determinism, UTF-8 sanitization; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.15 (2026-11-03, Kimi Code CLI, YaRN Qwen3/3.5); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02, /v1/decisions endpoint, watchdog stack dumps); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.1 (2026-10-30, Mistral Large 4 ~1T MoE, FP8 adapter training via PEFT)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.6 (2026-10-31): greatly reduced VRAM during quantization, DeepseekV41 + Lfm3 support; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.915-beta (2026-11-04): FP8 LoRA training, tile_mlp activation memory reduction, SDXL at 4GB VRAM, Qwen-Image speedups; RTX 4070 Ti relevant

## Worth studying

- [Aegis OS: A Transactional Multi-Tenant Runtime for Autonomous Coding Agents](https://arxiv.org/abs/2611.08516) — arXiv (2026-10-22): Rust-based MCP/A2A runtime; 0% ASR across 80 attacks, 94–99% prompt reduction. Open source, directly relevant for local coding agents.
- [I Think, Therefore I Attack: Thought Injection on Reasoning Agents](https://arxiv.org/abs/2611.08811) — arXiv (2026-11-06): novel attack on reasoning agents via thought-trace PI; 50% ASR vs 0% for standard PI. Essential for deploying reasoning agents.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-09.md) · [Latest weekly](reports/weekly/2026-W45.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
