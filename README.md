# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-3-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-20-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--25-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-25, daily)

- **ai-supplychain-001** PROMOTED emerging→accelerating: Microsoft agent-framework 1.26.1/1.26.2 on PyPI (Nov 17) — .pth startup-hook credential stealer targeting Azure/AWS/GitHub/Docker/HF; 2nd independent AI-package compromise after litellm. Attacker used Cairn AI pentest framework.
- **local-inference-001** (accelerating, held): 5 new llama.cpp CVEs (3 GGUF RCE-class, highest 8.5), 3 new vLLM GHSAs (2 High 8.7), 1 SGLang GHSA (first ever — High 8.7, unauth LoRA injection → potential RCE). Now ≥7 projects.
- **agentic-injection-001** (accelerating, held): Permission-reply policy rewriting in Claude Code, context compaction breaks agent authorization (91% attack success), MCP catalog weakest-link analysis (99% vulnerability at 200 tools).
- **agentic-offensive-ops-001** (emerging, held): Wiz/Elastic/Sysdig published follow-up posts (Nov 17-23) but direct URLs 404'd; queued.
- **llm-frontend-001** (emerging, held): no new advisories; dormancy warning at Nov 29.
- **Queue**: 20 live items; ai-supplychain-001 promotion criterion met.

## Trends

seed 0 · emerging 2 · accelerating 3 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-20](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-133710) — llama.cpp CVE-2026-133710 (8.5): hrm_text int overflow → heap OOB write/RCE; part of 5-CVE Nov batch + 3 vLLM GHSAs + first SGLang GHSA |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-24](https://arxiv.org/abs/2611.32195) — Permission Replies That Rewrite Coding-Agent Policy: deny-rule deletion bypasses Claude Code permission checks |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | accelerating | [2026-11-17](https://www.wiz.io/blog/malicious-version-of-microsofts-agent-framework-published-to-pypi) — Microsoft agent-framework PyPI compromise: .pth credential stealer, 2nd independent AI-package attack |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow CVE-2026-97677 (High 8.1): path traversal → arbitrary file read/write |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns (ARTEX, CyberStrikeAI)](TRENDS.md#trends) | emerging | [2026-11-13](https://www.elastic.co/security-labs/threat-command/agentic-offensive-frameworks-detection-artex) — Elastic Security Labs: 5 AI attack frameworks analyzed; ARTEX attributed to Storm-0940 |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12720 (2026-11-25); MCP image/audio in tool results, SVE OOB hardening; 5 new CVEs Nov 18-21 (3 GGUF RCE-class incl. CVE-2026-133710 heap OOB 8.5); security floor: ≥b12556 (CVE-2026-133710)
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.18 (2026-11-24, Inkling 2 DSpark, llama.cpp b12651); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.34.0 (2026-11-16, checkpoint/restore, extensible KV cache); 3 new GHSAs Nov 18 (2 High 8.7); security floor: ≥0.33.0 (CVE-2026-130685/130686)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v5.0.0 (2026-11-18, major: Python/shell sandbox, permission system, add-on architecture)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.126.0 (2026-11-18, code scanning, credential hardening); note: acquired by OpenAI (Mar 2026)
- **[transformers](https://github.com/huggingface/transformers)** — v5.24.1 (2026-11-24, Inkling 2 Mini, Dory, peft≥0.22.0; Jinja sandbox hardening in v5.22.2)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.1 (2026-11-18, packaging fix; v1.2.0: CoPyRIT GUI, GOAT/A2A targets, ASSERT scoring)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): multi-device quantization fix; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.924-beta (2026-11-24): Inkling 2 Mini LoRA/QLoRA fine-tuning (1.8–3.1x faster, ~50% less VRAM), speculative decoding, 8-12GB GPU offloading; RTX 4070 Ti relevant

## Worth studying

- [ReQOR: Operator-Discrepancy Subspace Repair for Quantization-Conditioned Backdoors](https://arxiv.org/abs/2611.32755) — arXiv (2026-11-24): training-free defense for quantization-activated backdoors; pairs with QHijack-LoRA attack. Practical for consumer-GPU quantized deployments.
- [When Answering Is Administering: Permission Replies That Rewrite Coding-Agent Policy](https://arxiv.org/abs/2611.32195) — arXiv (2026-11-24): Claude Code deny-rule deletion bypass with tight bounds and fix. Essential for deploying/red-teaming coding agents.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-25.md) · [Latest weekly](reports/weekly/2026-W46.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
