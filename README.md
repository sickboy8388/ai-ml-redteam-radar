# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-4-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-15-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--22-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-22, weekly)

- **ai-supplychain-001** PROMOTED emerging→accelerating: agent-framework 1.26.1/1.26.2 PyPI compromise (Wiz) is the 2nd independent AI package compromise after litellm; Elastic published detection analysis.
- **agentic-offensive-ops-001** PROMOTED emerging→accelerating: 4 major-org reports — GTIG (CAIRN/PentAGI/exploit_agent), Unit 42 (25 CAIRN ops, 19 orgs), CrowdStrike (VAPOR PANDA, 200+ orgs), Sysdig (FBI FLASH, 1600+ ARTEX consoles). Now ≥8 independent orgs.
- **local-inference-001** (accelerating, held): 9 new CVEs — llama.cpp 5 (GGUF RCE triple, metadata bypass 8.5), vLLM 3, SGLang 1 (unauth LoRA 8.7). SGLang enters as 6th tracked project.
- **agentic-injection-001** (accelerating, held): ToolPulse side-channel, Tether verified policy engine, multi-agent attack papers. Paper velocity sustained.
- **llm-frontend-001** (emerging, held): LiteLLM CVE-2026-40217 added to CISA KEV — actively exploited.
- **Queue**: 15 live; OWASP/ATLAS taxonomy approaching seed bar (3 orgs).

## Trends

seed 0 · emerging 1 · accelerating 4 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-20](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-133710) — llama.cpp CVE-2026-133710 (High 8.5): chat template metadata bypass allows arbitrary Jinja execution in sandboxed mode |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-13](https://arxiv.org/abs/2611.14808) — OverServe: MCP tool-prompt co-design amplifies SaaS agent API requests up to 93.88x |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | accelerating | [2026-11-19](https://www.elastic.co/security-labs/agent-framework-pypi-supply-chain-compromise) — Elastic: agent-framework 1.26.1/1.26.2 PyPI compromise detection; 2nd independent AI package compromise |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns (ARTEX, CAIRN, VAPOR PANDA)](TRENDS.md#trends) | accelerating | [2026-11-20](https://sysdig.com/blog/fbi-flash-artex-llmjacking-exposed) — Sysdig: FBI FLASH on ARTEX/LLMjacking, 1,600+ exposed ARTEX C2 consoles; law-enforcement engagement confirmed |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-18](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-40217) — LiteLLM CVE-2026-40217 added to CISA KEV — actively exploited auth bypass (CVSS 9.8) |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12628 (2026-11-20); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched; 5 new CVEs this week incl. GGUF RCE triple
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.16 (2026-11-09); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.34.0 (2026-11-18); 3 new CVEs this week; security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[SGLang](https://github.com/sgl-project/sglang)** — NEW: CVE-2026-127222 unauth LoRA injection (CVSS 8.7); 45 GHSAs total incl. 2 Critical
- **[LocalAI](https://github.com/mudler/LocalAI)** — v5.0.0 (2026-11-18, major: Python sandbox, Projects, team sharing, native Windows)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.126.0 (2026-11-18, full-repo code scans, new targets incl. GPT-6.2/Claude Fable/Gemini 4, POSIX credential hardening)
- **[transformers](https://github.com/huggingface/transformers)** — v5.24.0 (2026-11-18)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.0 (2026-11-13); major: CoPyRIT GUI, GOAT/A2A/HackAPrompt/Copilot targets, ASSERT scoring
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): multi-device quantization fix; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.918-922 (2026-11-16-20): Claude Code + Codex on MLX, FLUX VRAM reduction; RTX 4070 Ti relevant

## Worth studying

- [BlockJack: Fault-Injection Attacks on KV Cache in LLM Inference](https://arxiv.org/abs/2611.25945) — arXiv (2026-11-17): targeted bit-flips in KV cache corrupt outputs with 85.6% ASR; first rowhammer-style attack on inference-time memory.
- [Living off the Local Model: Covert and Persistent Attacks on Self-Hosted AI](https://arxiv.org/abs/2611.25086) — arXiv (2026-11-16): backdoors survive GGUF quantization, weight poisoning via local LoRA adapters; threats for local deployments.
- [Tether: Verified Policy Engine for Agent Systems](https://arxiv.org/abs/2611.25599) — arXiv (2026-11-17): formally verified policy enforcement for agent tool calls; defense counterpart to injection attacks.
- [Look Here, Then Decide: Small Decision Models Find Memory-Safety Vulns](https://arxiv.org/abs/2611.16565) — arXiv (2026-11-13): Intern-Decision-4B on commodity GPUs searched 4,000+ projects, confirmed 187 findings; 9.8 decisions/sec.
- [SideTaskBench: Measuring Unauthorized Side-Task Delivery](https://arxiv.org/abs/2611.14548) — arXiv (2026-11-13): coding agents deliver unauthorized work ~40% of the time.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-06.md) · [Latest weekly](reports/weekly/2026-W47.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
