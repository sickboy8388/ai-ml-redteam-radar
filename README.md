# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-3-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-20-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--26-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-26, daily)

- **ai-supplychain-001** PROMOTED emerging→accelerating: Microsoft agent-framework PyPI compromise (Nov 17) — SECOND independent .pth credential stealer after litellm; attacker tooling identified as Cairn AI pentesting framework. Now 3 package-level compromises across ≥4 orgs.
- **local-inference-001** (accelerating, held): 3 llama.cpp ZDI RCE CVEs (GGUF parsing integer overflow + heap overflow, CVSS 7.8), plus 3 more llama.cpp CVEs, 3 vLLM GHSAs, and 1 SGLang CVE — 17 CVEs across the stack in 14 days.
- **agentic-injection-001** (accelerating, held): Chasm latent KV-cache transfer attack reaches 92.5% ASR; recovery-induced workflow security downgrade silently drops protections (novel attack class).
- **agentic-offensive-ops-001** (emerging, held): Datadog Security Labs independently confirms ARTEX in AWS with IoCs; Cairn linked to real supply-chain attack via agent-framework compromise.
- **llm-frontend-001** (emerging, held): no new advisories (18 days); approaching 21-day dormancy threshold.
- **Queue**: 20 live; 7 new items added (Claude Code secrets leak, Elastic AI detection rules, Anthropic disclosure policy, Unsloth consumer-GPU activity).

## Trends

seed 0 · emerging 2 · accelerating 3 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-25](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-137057) — llama.cpp CVE-2026-137057: grammar parser integer underflow → remote DoS; part of 6-CVE llama.cpp batch incl. 3 ZDI RCEs |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-26](https://arxiv.org/abs/2611.34278) — Chasm: cross-model KV-cache transfer breaks safety alignment; 92.5% ASR via mapper optimization |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | accelerating | [2026-11-17](https://www.wiz.io/blog/malicious-version-of-microsofts-agent-framework-published-to-pypi) — Microsoft agent-framework PyPI compromise: .pth credential stealer, Cairn framework; 2nd package attack after litellm |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow CVE-2026-97677 (High 8.1): path traversal → arbitrary file read/write |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns (ARTEX, CyberStrikeAI)](TRENDS.md#trends) | emerging | [2026-11-17](https://www.wiz.io/blog/malicious-version-of-microsofts-agent-framework-published-to-pypi) — Cairn AI pentesting framework identified as attacker tooling in real supply-chain attack |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12760 (2026-11-26); 6 new CVEs Nov 18-25 incl. 3 ZDI RCEs (GGUF parsing); security floor: ≥b12604 (CVE-2026-137057 grammar parser DoS)
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.18 (2026-11-24); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.34.0 (2026-11-16); 3 new GHSAs Nov 18 (2 High: media budget exhaustion 8.7, input validation crash 8.7); security floor: ≥0.33.0 (CVE-2026-130685 EngineCore crash)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.126.0 (2026-11-18); credential security improvements (POSIX restrictions, Azure redaction)
- **[transformers](https://github.com/huggingface/transformers)** — v5.24.1 (2026-11-24, vLLM compat, Llama4/Dory fixes; v5.24.0 adds Inkling 2 Mini NVFP4/MXFP8)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.1 (2026-11-18); packaging fix for v1.2.0 (CoPyRIT GUI, GOAT/A2A/HackAPrompt targets, ASSERT scoring)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): multi-device quantization fix, pipelined prefill; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.925-beta (2026-11-25): Inkling 2 Mini fine-tuning on 8-12GB GPUs, QLoRA 25% faster, diffusion LoRA on T4, AMD NPU; RTX 4070 Ti relevant

## Worth studying

- [AgentLens: Graph-guided Security Auditing for LLM-based Agents](https://arxiv.org/abs/2611.34380) — arXiv (2026-11-26): pre-deployment auditing framework; found 44 confirmed vulnerabilities (12 CVEs) in 5 widely-used agent apps; 3.67x more vulns than AgentFuzz.
- [The Detour Is the Danger: Preserving Security During LLM Agent Recovery](https://arxiv.org/abs/2611.33605) — arXiv (2026-11-26): induced failures cause agents to silently drop security protections; ARGUS prevents all protection-loss events. Novel attack class.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-26.md) · [Latest weekly](reports/weekly/2026-W46.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
