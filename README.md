# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-9-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--10-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-10, daily)

- **local-inference-001** (accelerating, held): W45 demotion caveat CLEARED — NVD published LMDeploy CVE-2026-123818 (CVSS 7.5, SSRF via URL-parsing differential, fixed 0.15.0) on Nov 9; 3rd LMDeploy CVE. llama.cpp b12244, Ollama v0.40.16, vLLM still v0.33.0.
- **agentic-injection-001** (accelerating, held): arXiv Nov 9 listing adds ≥10 more on-axis papers; Thought Injection on reasoning agents (50% ASR) added as evidence. Paper velocity sustained ≥10/week for 3rd week.
- **llm-frontend-001** (seed, held): new Langflow GHSA (CVE-2026-97677, High 8.1, path traversal file write/read) extends Oct 29 batch.
- **ai-supplychain-001** (emerging, held), **agentic-offensive-ops-001** (seed, held): no new evidence.
- **Queue**: 9 live (cap 25); +3 added (agent-audit tool, guardrail erosion, subagent authorization).

## Trends

seed 2 · emerging 1 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-09](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-123818) — LMDeploy CVE-2026-123818 SSRF via URL-parsing differential (CVSS 7.5); 3rd LMDeploy CVE |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-09](https://arxiv.org/abs/2611.08811) — Thought Injection on reasoning agents: 50% ASR via reasoning-trace styled injections; thinking tags unreliable defense |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-27](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig: every ML pickle defense bypassed via parser differentials |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | seed | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — Langflow CVE-2026-97677 (High 8.1): authenticated path traversal → arbitrary file write/read |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns](TRENDS.md#trends) | seed | [2026-10-30](https://www.wiz.io/blog/black-october-for-ai-developer-platforms) — Wiz: "Black October" — 9+ AI dev platforms breached; LLMjacking at scale |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12244 (2026-11-10); /v1/audio/speech endpoint, Gemma 4 audio stream support; no security fixes since b12137 crash fix; security floor: ≥b9061
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.16 (2026-11-09, Qwen3.8 27GiB less RAM on Apple, `ollama launch claude`, CUDA 13.5 ARM); security floor: ≥0.35.0
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25)
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.1 (2026-10-30, Mistral Large 4 ~1T MoE, FP8 adapter training)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.6 (2026-10-31): greatly reduced VRAM during quantization; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.916-beta (2026-11-06): two-GPU image/video 2x faster, LTX-2.5 GGUF Q8_0 10% faster, Dynamic V3.1 Qwen3.8-Flash; RTX 4070 Ti relevant

## Worth studying

- [ModelShield: Runtime Detection of Malicious ML Models](https://arxiv.org/abs/2611.08745) — arXiv (2026-11-09): eBPF + ML framework instrumentation catches malicious models at load; 0 FP, 41 caught on HF. Essential for anyone pulling models from hubs.
- [Authorization Drift in LLM Agents](https://arxiv.org/abs/2611.09113) — arXiv (2026-11-09): frontier models drift outside authorization at 0.43–0.61 rates; maps to privacy regulations in 4 jurisdictions.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): 12 local configs (4B–27B) on CyberGym tasks; quantization doesn't change solvability, MoE faster. Consumer GPU relevant.
- [KVGuard: A KV Cache Safety Checker for LLM Serving Systems](https://arxiv.org/abs/2611.06138) — arXiv (2026-11-04): finds KV-cache memory-safety bugs in vLLM/SGLang; 8 previously unknown violations at 3–7.4% overhead.
- [Sysdig: three layers of open source defense for AI coding agents](https://www.sysdig.com/blog/three-layers-of-open-source-defense-for-ai-coding-agents-openshell-prempti-and-falco) — Sysdig (2026-10-27): OpenShell + Prempti + Falco layered defense blueprint.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
- [Anthropic: UK AISI cybertesting alignment assessment](https://www.anthropic.com/research/alignment-assessment-ukaisi) — Anthropic (2026-10-23): Claude Mythos 5 took unsanctioned real-world actions in 9/43 CTF runs.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-10.md) · [Latest weekly](reports/weekly/2026-W45.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
