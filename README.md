# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-7-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--02-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-02, daily)

- **NEW TREND: agentic-offense-001** (seed): Wiz published two landmark reports — "Rise of Agentic Attacks" (Oct 29: ARTEX/Storm-0940, Hermes, CrowdStrike 4 actors, 7 fingerprints) and "Black October" (Oct 30: 9 AI dev platforms attacked via agent swarms, LLMJacking at scale, $371k crypto theft, $100k+ Bedrock abuse). First trend on axis 4.
- **llm-frontend-001 PROMOTED seed→emerging**: Langflow disclosed 25 new advisories Oct 29 (6 Critical CVSS 9.8 including auth bypass and code injection); LiteLLM added 3 new GHSAs Oct 27 (High priv-escalation to admin+RCE via salt-key reuse). Now 6 independent projects.
- **agentic-injection-001** (accelerating, held): arXiv cs.CR Nov 2 listing carries ~15 more agent-security papers — SecPO best-yet PI defense, tool-call privacy leakage, hijack detector audit, agent memory robustness, elastic least privilege, and more.
- **local-inference-001** (accelerating, held): llama.cpp b12032, Ollama v0.40.13 (LFM3), no new CVEs.
- **ai-supplychain-001** (emerging, held): module-shadowing paper shows 51%/87% payload execution in LLM agents.
- **Queue**: 7 live items; 5 resolved/promoted (autonomous-agent cluster → agentic-offense-001, ARTEX, LLMjacking, vLLM batch, arXiv backlog). Anchoring warning BROKEN — first new trend seeded since W43.

## Trends

seed 1 · emerging 2 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-28](https://github.com/advisories/GHSA-6757-hggm-hp2w) — vLLM High: forged SHM handle reaches pickle.loads; Oct 27-28 batch incl. code_revision RCE |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-23](https://arxiv.org/abs/2610.31404) — AgentPhishing: 4/9 agents detect <10% of adaptive phishing, comply >45% |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-27](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig: every ML pickle defense bypassed via parser differentials |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-10-29](https://github.com/advisories/GHSA-vfwm-g9g9-v2g5) — Langflow 25-advisory batch (6 Critical CVSS 9.8): auth bypass + code injection; LiteLLM priv escalation to admin+RCE |
| [AI-agent weaponization & agentic cloud attacks (ARTEX, Black October, LLMJacking)](TRENDS.md#trends) | seed | [2026-10-30](https://www.wiz.io/blog/black-october-for-ai-developer-platforms) — Wiz: 9 AI dev platforms attacked in Oct 2026; agent swarms, LLMJacking at scale |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12032 (2026-11-01); OpenCL iq3, LFM3 tensor split, server prefix cap; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.13 (2026-10-28: LFM3-audio/omni on Linux+Windows); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18, 3 security fixes, NVFP4 KV cache on Ada GPUs); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.2 (2026-10-19)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — 1.6.6 (2026-10-31): greatly reduced VRAM during quantization, faster quant capture, DeepseekV41+LFM3 support; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.913-beta (2026-10-30): batched MoE fine-tuning, Qwen-Image 2x faster under 16GB, FLUX.2-klein on ~12.7GB RAM, DeepSeek-V4.1-Flash GGUFs; sandboxing (0.1.912)

## Worth studying

- [Wiz: Rise of Agentic Attacks](https://www.wiz.io/blog/the-rise-of-agentic-attacks) — Wiz (2026-10-29): ARTEX/Storm-0940, Hermes, 7 fingerprints of agentic behavior, 3 Wiz-investigated cases; essential landscape overview for defending against AI-agent-driven intrusions.
- [SecPO: Principled Adversarial Training for Prompt Injection Security](https://arxiv.org/abs/2610.41998) — arXiv (2026-10-30): best reported PI defense — SecPO loss + adversarial training cuts ASR substantially vs Meta-SecAlign with minimal utility loss.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-02.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
