# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-4-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-16-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--22-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-22, daily)

- **ai-supplychain-001** PROMOTED emerging→accelerating: Microsoft agent-framework 1.26.1/1.26.2 on PyPI (Nov 17) carried .pth credential stealer — 2nd major AI package compromise after litellm; Wiz analysis opened.
- **agentic-offensive-ops-001** PROMOTED emerging→accelerating: Sysdig TRT (Nov 20) documented VAPT + ARTEX with FBI FLASH advisory; ≥5 independent orgs over 4 weeks.
- **local-inference-001** (accelerating, held): 3 ZDI llama.cpp GGUF parsing RCE CVEs (Nov 18) + SGLang unauth LoRA→RCE (CVE-2026-127222) + 3 new vLLM GHSAs; vLLM v0.34.0; now ≥7 projects.
- **agentic-injection-001** (accelerating, held): ToolPulse side-channel eavesdropping on tool-using agents (>93% F1). Paper velocity ≥10/week, 5th week.
- **llm-frontend-001** (emerging, held): no new advisories.
- **Queue**: 16 live; 2 promotions to accelerating today.

## Trends

seed 0 · emerging 1 · accelerating 4 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-18](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-126974) — llama.cpp 3 ZDI GGUF parsing RCE CVEs + SGLang CVE-2026-127222 unauth LoRA→RCE (8.7) + 3 new vLLM GHSAs |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-20](https://arxiv.org/abs/2611.25470) — ToolPulse: cache side-channel eavesdropping reconstructs LLM agent tool workflows with >93% F1 |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | accelerating | [2026-11-17](https://www.wiz.io/blog/malicious-version-of-microsofts-agent-framework-published-to-pypi) — Microsoft agent-framework .pth credential stealer; 2nd major AI package compromise |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns (ARTEX, CyberStrikeAI, VAPT)](TRENDS.md#trends) | accelerating | [2026-11-20](https://www.sysdig.com/blog/artex-and-the-offensive-tool-powered-by-llmjacking-five-months-earlier) — Sysdig TRT: VAPT + ARTEX; FBI FLASH; 1,600+ exposed consoles; LLMjacking funds agentic offense |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow CVE-2026-97677 (High 8.1): path traversal → arbitrary file read/write |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12628 (2026-11-22); 3 ZDI RCE CVEs disclosed Nov 18 (GGUF parsing, fixed ≥v1.0.0); security floor: ≥v1.0.0; note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.17 (2026-11-10, Inkling 2 Mini, Apple silicon multi-request); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.34.0 (2026-11-16); ReDoS fix, bounded audio, chat template control; 3 new GHSAs Nov 18 (2 High 8.7); security floor: ≥0.33.0
- **[LocalAI](https://github.com/mudler/LocalAI)** — v5.0.1 (2026-11-20, major: desktop app, Projects, Files, team sharing, add-ons)
- **[SGLang](https://github.com/sgl-project/sglang)** — CVE-2026-127222 (High 8.7): unauth LoRA adapter loading → RCE; fix commit 7b5fb39
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25)
- **[transformers](https://github.com/huggingface/transformers)** — v5.24.0 (2026-11-21, Inkling 2 Mini, Apertus 1.5, past_key_values→cache rename, peft≥0.22.0); Jinja sandbox hardening in v5.22.2
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.1 (2026-11-18, packaging fix); v1.2.0 (Nov 13): CoPyRIT GUI, GOAT/A2A/HackAPrompt/Copilot targets, ASSERT scoring
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): multi-device quantization fix, pipelined prefill; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.922-beta (2026-11-20): Inkling 2 Mini 26B/5.4B-active, AMD NPU Q4NX, GGUF image 52-66% less RAM, INT8/FP8 on older NVIDIA cards; RTX 4070 Ti relevant

## Worth studying

- [Tether: Verified Stateful Policy Engine for Agent Monitoring](https://arxiv.org/abs/2611.25599) — arXiv (2026-11-20): Lean 4-verified policy engine blocks 100% in-scope attacks at <5% FPR; practical blueprint for securing deployed AI agents.
- [Living off the Local Model: Browser-Embedded LMs for Post-Exploitation](https://arxiv.org/abs/2611.25086) — arXiv (2026-11-20): Gemini Nano in Chrome used for credential extraction, PII triage, image analysis — no network egress for inference. New LOTL vector.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-22.md) · [Latest weekly](reports/weekly/2026-W46.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
