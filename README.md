# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-3-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-20-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--20-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-20, daily)

- **ai-supplychain-001** PROMOTED emerging→accelerating: Microsoft agent-framework 1.26.1/1.26.2 on PyPI (Nov 17) — .pth credential stealer targeting Azure/ADO/GitHub Actions; attacker used Cairn AI pentesting framework; ~200k monthly downloads. Second major AI package compromise after LiteLLM.
- **local-inference-001** (accelerating, held): llama.cpp ZDI batch — 3 new GGUF RCE CVEs (Nov 18, integer/heap overflow); SGLang CVE-2026-127222 — first SGLang CVE (missing auth + LoRA RCE); vLLM 3 more GHSAs (2 High, 1 Moderate). Now ≥7 projects with advisories.
- **agentic-offensive-ops-001** (emerging, held): Cairn framework confirmed used in real supply-chain attack (Wiz agent-framework compromise); Living off the Local Model — Chrome's Gemini Nano abused for post-exploitation.
- **agentic-injection-001** (accelerating, held): no new direct evidence; arXiv Nov 20 listing carries ToolPulse side-channel and ROGUE-AI replication study → queued.
- **llm-frontend-001** (emerging, held): no new advisories.
- **Queue**: 20 live; 7 new items added (ToolPulse, ROGUE-AI, Anthropic CVD, Sysdig MCP Server, Question Then Affirm, ALIoTh, SoK LLM vulns).

## Trends

seed 0 · emerging 2 · accelerating 3 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-18](https://github.com/advisories/GHSA-935v-h6wh-q726) — llama.cpp ZDI batch: 3 GGUF parsing RCE CVEs (integer overflow, heap overflow, MTMD overflow); coordinated via ZDI |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-13](https://arxiv.org/abs/2611.14808) — OverServe: MCP tool-prompt co-design amplifies SaaS agent API requests up to 93.88x |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | accelerating | [2026-11-17](https://www.wiz.io/blog/malicious-version-of-microsofts-agent-framework-published-to-pypi) — Microsoft agent-framework PyPI compromise: Cairn AI framework used; .pth stealer for Azure/ADO creds; 2nd major package compromise |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow CVE-2026-97677 (High 8.1): path traversal → arbitrary file read/write |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns (ARTEX, CyberStrikeAI)](TRENDS.md#trends) | emerging | [2026-11-18](https://arxiv.org/abs/2611.25086) — Living off the Local Model: Chrome's Gemini Nano abused for post-exploitation; Cairn framework confirmed in real supply-chain attack |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12559 (2026-11-20); b12556 HRM integer overflow memory-safety fix; **3 new ZDI RCE CVEs (Nov 18)**: CVE-2026-126974/5/6; security floor: ≥b9061 (CVE-2026-43631 UAF); note: Cyera bugs + ZDI batch = growing GGUF parser attack surface
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.16 (2026-11-09); v0.40.17-rc2 pre-release (Nov 10); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.34.0 (2026-11-16, checkpoint/restore, dep floors raised); 3 new GHSAs Nov 18 (2 High: media budget DoS, token ID crash); security floor: ≥0.33.0 (CVE-2026-130685/6 DoS)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v5.0.0 (2026-11-18, major: sandboxed code execution, add-ons, default-off permissions, sharing controls)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.126.0 (2026-11-18); GPT-6.2/Claude Fable/Gemini 4 models, derived-metric sandboxing, security hardening
- **[transformers](https://github.com/huggingface/transformers)** — v5.23.0 (2026-11-13, Inkling2 594B/17B-active, LFM3-VL, ExportedModel API, Jinja sandbox hardening in v5.22.2)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.1 (2026-11-18, packaging fix); v1.2.0 (Nov 13): CoPyRIT GUI, GOAT/A2A/HackAPrompt/Copilot targets, ASSERT scoring
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): multi-device quantization fix, pipelined prefill; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.920-beta (2026-11-19): AMD NPU, QLoRA 25% faster, diffusion LoRA 42% faster, MiniMax-H3-Image on 8GB GPUs; RTX 4070 Ti relevant
- **[SGLang](https://github.com/sgl-project/sglang)** — CVE-2026-127222 (Nov 18, High): missing auth on LoRA endpoint + RCE via deserialization; first tracked advisory

## Worth studying

- [BlockJack: Cross-Tenant KV Cache Fault Attacks on LLM Serving](https://arxiv.org/abs/2611.25945) — arXiv (2026-11-19): first fault attack on vLLM/SGLang block tables via Rowhammer; cross-tenant data exposure, up to 41.1% misdiagnosis on medical benchmark; vLLM and Sonar confirmed and patched.
- [Living off the Local Model: Abusing Browser-Embedded LLMs for Post-Exploitation](https://arxiv.org/abs/2611.25086) — arXiv (2026-11-18): Chrome's Gemini Nano driven from host interpreters for credential extraction, PII detection, staged exfiltration; novel LOL technique using vendor-signed model.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-20.md) · [Latest weekly](reports/weekly/2026-W46.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
