# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-3-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-19-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--21-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-21, daily)

- **ai-supplychain-001** PROMOTED emerging→accelerating: Microsoft agent-framework PyPI compromise (Nov 17) — .pth credential stealer targeting Azure/CI/Docker/HF tokens; attacker used "Cairn" AI pentesting framework; SECOND independent package compromise after litellm. Wiz primary, Elastic detected in 6 minutes.
- **local-inference-001** (accelerating, held): llama.cpp ZDI batch (Nov 18) — 3 GGUF parsing RCE flaws from Trend Micro ZDI + CVE-2026-133710 (Nov 20, hrm_text int overflow 8.5). SGLang FIRST advisory: CVE-2026-127222 (High 8.7, unauth LoRA loading → RCE chain). vLLM Nov 18 batch (3 more CVEs). Now ≥8 projects.
- **agentic-injection-001** (accelerating, held): ToolPulse side-channel reconstructs agent tool workflows F1>93%; ROGUE-AI reproduces 108 real agent incidents (89% fidelity); Tether verified policy engine blocks 100% in-scope attacks. Paper velocity ≥10/week for 5th week.
- **agentic-offensive-ops-001** (emerging, held): Sysdig TRT confirms FBI FLASH on ARTEX; 1600+ exposed consoles; Amazon Threat Intelligence involvement; 5th independent org. Agent-framework compromise used Cairn.
- **llm-frontend-001** (emerging, held): no new advisories; 13 days since last evidence, dormancy at 21 days.
- **Queue**: 19 live; 7 new items added.

## Trends

seed 0 · emerging 2 · accelerating 3 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-20](https://github.com/advisories/GHSA-92hv-w2fh-9w89) — llama.cpp CVE-2026-133710 (High 8.5): hrm_text loader integer overflow → heap corruption → potential RCE; ZDI batch adds 3 more GGUF parsing RCE flaws |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-19](https://arxiv.org/abs/2611.25470) — ToolPulse: cache-based side-channel reconstructs tool workflows of LLM agents with F1>93% across 11 models |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | accelerating | [2026-11-17](https://www.wiz.io/blog/malicious-version-of-microsofts-agent-framework-published-to-pypi) — Microsoft agent-framework PyPI compromise: .pth credential stealer, ESRP cert compromised, attacker used Cairn AI pentesting framework |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow CVE-2026-97677 (High 8.1): path traversal → arbitrary file read/write |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns (ARTEX, CyberStrikeAI)](TRENDS.md#trends) | emerging | [2026-11-20](https://www.sysdig.com/blog/artex-and-the-offensive-tool-powered-by-llmjacking-five-months-earlier) — Sysdig TRT: ARTEX/LLMjacking analysis; FBI FLASH confirms 1600+ exposed consoles; Amazon Threat Intelligence involved |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12602 (2026-11-21); GGML major version bump, Inkling 2 Mini support, Gemma4 optimized prefill; security: 4 new ZDI GHSAs Nov 18-20 (GGUF parsing RCE); security floor: ≥b12556 (CVE-2026-133710)
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.17 (2026-11-10, Inkling 2 Mini, Apple silicon multi-request serving); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.34.0 (2026-11-16, extensible KV cache default, Blackwell perf gains); 3 new GHSAs Nov 18 (2 High); security floor: ≥0.33.0 (CVE-2026-130686 media budget DoS)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v5.0.0 (2026-11-18, **major**: desktop app macOS/Linux, Python/shell sandbox, Projects, team sharing) + v5.0.1 (2026-11-20, ROCm 10.1 default)
- **[SGLang](https://github.com/sgl-project/sglang)** — CVE-2026-127222 (High 8.7, Nov 18): unauth LoRA adapter loading → potential RCE via deser bypass; ≤0.5.23
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.126.0 (2026-11-18)
- **[transformers](https://github.com/huggingface/transformers)** — v5.23.0 (2026-11-13, Inkling2, LFM3-VL, ExportedModel API)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.1 (2026-11-18, packaging fix); v1.2.0 (Nov 13): CoPyRIT GUI, GOAT/A2A/HackAPrompt/Copilot targets, ASSERT scoring
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): multi-device quantization fix, pipelined prefill; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.922-beta (2026-11-20): Inkling 2 Mini 26B on 16GB RAM, GGUF image models 52-66% less RAM, QLoRA 25% faster, AMD NPU support; RTX 4070 Ti relevant

## Worth studying

- [Living off the Local Model: Abusing Browser-Embedded Language Models for Post-Exploitation](https://arxiv.org/abs/2611.25086) — arXiv (2026-11-18): Gemini Nano in Chrome as post-exploitation engine; credential extraction, archive unlocking, key staging — all without user interaction. Local-model threat surface.
- [SoK: Assessing the Evolution of LLM Capability in Software Vulnerability Research](https://arxiv.org/abs/2611.26601) — arXiv (2026-11-19): open-weight models reached discovery/validation autonomy; disclosed vulns doubled in 2026 with growing share high/critical.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-21.md) · [Latest weekly](reports/weekly/2026-W46.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
