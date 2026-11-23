# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-3-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-18-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--23-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-23, daily)

- **ai-supplychain-001** PROMOTED emerging→accelerating: Microsoft agent-framework 1.26.1/1.26.2 compromised on PyPI (Nov 17, Wiz primary) — .pth credential stealer targeting Azure/CI/HF tokens, attacker used stolen ESRP cert, tooling identified as "Cairn" AI pentesting framework. Second major AI-stack package compromise after litellm, meeting the stated accelerating criterion.
- **local-inference-001** (accelerating, held): llama.cpp gets 3 ZDI-reported GGUF parsing RCEs (Nov 18, CVSS 7.0–7.8) + hrm_text heap corruption (Nov 20, CVSS 8.5); vLLM adds 3 CVEs (2× CVSS 8.7 High); SGLang enters with CVE-2026-127222 (CVSS 8.7, missing auth → RCE). Now ≥7 projects with advisories.
- **agentic-injection-001** (accelerating, held): arXiv Nov 23 carries GRAFT (MCP description poisoning evading 5 defenses), Epistemic Guard (MCP receipt proxy), Markdown Is Not a Firewall, Correct Precedents (on-device policy violations), SplitBench (benchmark privilege separation). Paper velocity ≥5/week, 5th consecutive week.
- **agentic-offensive-ops-001** (emerging, held): AWS Threat Intelligence + SentinelOne + FBI FLASH on ARTEX found via search but primaries not fully opened; queued.
- **Queue**: 18 live; new entries for AWS/Elastic/SentinelOne ARTEX coverage, Autonomous Parameter Surgery (LLM-driven backdoor implantation), TrojanMaxxing (one-shot VLM backdoors), Cleave (guardrail removal).

## Trends

seed 0 · emerging 2 · accelerating 3 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-20](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-133710) — llama.cpp CVE-2026-133710 (High 8.5): hrm_text integer overflow → heap corruption; 5 new llama.cpp CVEs + 3 vLLM + 1 SGLang this week |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-23](https://arxiv.org/abs/2611.27041) — GRAFT: LLM-optimized MCP tool-description poisoning evades 5 filter-based defenses |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | **accelerating** ⬆ | [2026-11-17](https://www.wiz.io/blog/malicious-version-of-microsofts-agent-framework-published-to-pypi) — Microsoft agent-framework PyPI compromise: .pth credential stealer, Cairn AI-pentesting tooling, quarantined in 55 min |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow CVE-2026-97677 (High 8.1): path traversal → arbitrary file read/write |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns (ARTEX, CyberStrikeAI)](TRENDS.md#trends) | emerging | [2026-11-13](https://www.elastic.co/security-labs/threat-command/agentic-offensive-frameworks-detection-artex) — Elastic Security Labs: 5 AI attack frameworks analyzed; ARTEX attributed to Storm-0940 |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12649 (2026-11-23); **5 new CVEs Nov 18-21**: 3 ZDI GGUF RCEs (CVE-2026-126974/126975/126976, CVSS 7.0–7.8), hrm_text heap corruption (CVE-2026-133710, CVSS 8.5), grammar_triggers input validation (CVE-2026-134540); security floor: ≥b12556
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.17 (2026-11-21, no security fixes); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.34.0 (2026-11-16); 3 new CVEs Nov 18 (2× CVSS 8.7 High DoS, 1× Moderate path traversal); security floor: ≥0.33.0
- **[SGLang](https://github.com/sgl-project/sglang)** — CVE-2026-127222 (High, CVSS 8.7): missing auth on LoRA endpoint → unauthenticated RCE; fixed commit 7b5fb39
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25)
- **[transformers](https://github.com/huggingface/transformers)** — v5.24.0 (2026-11-21, Inkling 2 Mini with NVFP4/MXFP8 quantized layers, Apertus 1.5, WavTokenizer)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.1 (2026-11-18, packaging fix); v1.2.0 major: CoPyRIT GUI, GOAT/A2A targets, ASSERT scoring
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): multi-device quantization, pipelined prefill; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.922-beta (2026-11-20): GGUF image models 52–66% less RAM, MiniMax-H3-Image on 8GB GPUs, QLoRA 25% faster, SDXL LoRA 28–31% faster; RTX 4070 Ti relevant

## Worth studying

- [GRAFT: Defense-Evading Metadata Poisoning in LLM Agents](https://arxiv.org/abs/2611.27041) — arXiv (2026-11-23): MCP tool-description poisoning via masking + iterative mutation; evades 5 filter defenses and adaptive defenses. Essential for auditing MCP server descriptions.
- [Autonomous Parameter Surgery: How LLMs Implant Selective Backdoors](https://arxiv.org/abs/2611.27920) — arXiv (2026-11-23): DeepSeek Flash edits model weights for 99.2% ASR at ~$1.74/run; training-free backdoor injection threat model.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-23.md) · [Latest weekly](reports/weekly/2026-W46.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
