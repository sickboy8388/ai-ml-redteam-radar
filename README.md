# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-10-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--04-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-04, daily)

- **NEW: agentic-offense-001** (seed): Wiz documents 6+ real-world agentic attack cases; ARTEX framework used by Storm-0940 against 2,250+ tenants; "Black October" saw 9+ AI developer platforms breached; Sysdig confirms ARTEX and DIVD AI-agent breach independently.
- **llm-frontend-001 PROMOTED seed→emerging**: IBM Langflow OSS discloses 25 GHSAs (6 Critical CVSS 9.8 incl. unauth RCE); LiteLLM CVE-2026-114612 priv escalation to admin via salt-key reuse → MCP stdio RCE. Now 6 independent projects.
- **agentic-injection-001** (accelerating, held): arXiv Nov 4 listing has 12+ on-axis papers — 3rd consecutive listing with ≥10; BrainwashedLLM jailbreak ASR 0.74-0.98, Voluntary Servitude NeurIPS 2026, nine-dimension PI taxonomy.
- **local-inference-001** (accelerating, held); **ai-supplychain-001** (emerging, held).
- **Queue**: 10 live items; ARTEX and LLMjacking promoted to new trend. Study shelf: +2 (Voluntary Servitude, LoRA-Patch).

## Trends

seed 1 · emerging 2 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-28](https://github.com/advisories/GHSA-6757-hggm-hp2w) — vLLM High: forged SHM handle reaches pickle.loads; Oct 27-28 batch incl. code_revision RCE |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-22](https://arxiv.org/abs/2610.31404) — AgentPhishing: 4/9 agents detect <10% of adaptive phishing, comply >45% |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-27](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig: every ML pickle defense bypassed via parser differentials |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-10-29](https://github.com/advisories/GHSA-vfwm-g9g9-v2g5) — IBM Langflow OSS 25-advisory batch: 6 Critical (unauth RCE, auth bypass, CVSS 9.8) |
| [AI-agent-assisted offensive operations (ARTEX, agentic intrusions, AI platform targeting)](TRENDS.md#trends) | seed | [2026-11-03](https://sysdig.com/blog/security-briefing-october-2026) — Sysdig: ARTEX/Storm-0940 + AI agent breaches DIVD via Zammad CVEs |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12099 (2026-11-04); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.14 (stable, 2026-11-03), v0.40.15-rc0 (pre-release, CUDA in-process); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02, new /v1/decisions endpoint by default, CUDA 12.9 dropped); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.1 (2026-10-30); v5.22.0 adds Mistral Large 4 (1T/52B-active, 1M ctx) + FP8 LoRA training
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — 1.6.6 (2026-10-31): greatly reduced VRAM during quantization, disk cache eviction fix; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.914-beta (2026-11-03): tile_mlp reduces MLP activation memory during training, CPU text fine-tuning, multi-LoRA batching, v0.1.912 safety fix (tool calls hitting output limit)

## Worth studying

- [Voluntary Servitude: Weaponized Safety Warnings for Controlling AI Agents](https://arxiv.org/abs/2611.04393) — arXiv, NeurIPS 2026 (2026-11-03): fabricated hazards steer agents through their own harm-avoidance reasoning at 60.4%; corroboration requirement removes ~95% of exposure.
- [LoRA-Patch: Defending Against Backdoored LoRA Adapters](https://arxiv.org/abs/2611.03752) — arXiv (2026-11-02): lightweight defense against backdoored LoRA adapters via directional steering; patches in <20s. Practical for anyone pulling third-party adapters for local fine-tuning.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
- [NameTrap: Steering AI Coding Agents Toward Security Vulnerabilities via Variable Names](https://arxiv.org/abs/2610.34253) — arXiv (2026-10-25): poisoned identifier names steer 6 coding agents toward CWE weaknesses (22-56% ASR); practical threat for anyone using AI assistants with untrusted repos.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-04.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
