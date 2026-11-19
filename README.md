# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-3-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-18-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--19-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-19, daily)

- **ai-supplychain-001** PROMOTED emerging→accelerating: Wiz reports malicious agent-framework 1.26.1/1.26.2 on PyPI — .pth credential stealer (same technique as litellm). Second independent AI-tooling package compromise meets the promotion criterion.
- **local-inference-001** (accelerating, held): 7 new CVEs across 3 projects — llama.cpp 3 ZDI GGUF RCE (High 7.0-7.8), vLLM 3 more (High 8.7 x2), SGLang CVE-2026-127222 (High 8.7, unauth LoRA injection → RCE, public PoC). SGLang is 8th project; ZDI is new reporting org.
- **agentic-injection-001** (accelerating, held): ~40+ on-axis arXiv papers Nov 14-19 (5th consecutive extreme-velocity week). Defense frameworks now dominate: SkillCFI blocked all 240 violations at ~2% overhead.
- **agentic-offensive-ops-001** (emerging, held): Compositional Exploits paper — coding agents chain harmless calls into attacks 72-84%, scanners detect 0%.
- **Queue**: 18 live; 5 new items added.

## Trends

seed 0 · emerging 2 · accelerating 3 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-18](https://github.com/advisories/GHSA-m386-99gj-pq7p) — SGLang CVE-2026-127222 (High 8.7): unauth LoRA injection → RCE as root; first SGLang advisory; 8th project in trend |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-18](https://arxiv.org/abs/2611.24185) — SkillCFI: control-flow integrity for agent skills; blocked all 240 violations at ~2% overhead |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | accelerating | [2026-11-17](https://www.wiz.io/blog/malicious-version-of-microsofts-agent-framework-published-to-pypi) — Wiz: malicious agent-framework 1.26.1/1.26.2 on PyPI; .pth credential stealer; 2nd AI-tooling package compromise after litellm |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow CVE-2026-97677 (High 8.1): path traversal → arbitrary file read/write |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns (ARTEX, CyberStrikeAI)](TRENDS.md#trends) | emerging | [2026-11-18](https://arxiv.org/abs/2611.19764) — Compositional Exploits: coding agents chain harmless tool calls into attacks 72-84%; single-tool scanners detect 0% |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12532 (2026-11-19); b12527 security fix (GGUF OOB read rejection); 3 ZDI GGUF RCE GHSAs Nov 18; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.16 (2026-11-09); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.34.0 (2026-11-16); 3 new GHSAs Nov 18 (2 High); security floor: ≥0.33.0 (CVE-2026-130685/130686 + earlier CVE-2026-114053)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v5.0.0 (2026-11-18, major: sandboxed bash tool, saved agents off-by-default, macOS notarized)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.126.0 (2026-11-18, credential protection, Azure connection string redaction); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.23.0 (2026-11-13, Inkling2 594B/17B-active, LFM3-VL, ExportedModel API, Jinja sandbox hardening in v5.22.2)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.1 (2026-11-18, packaging fix); v1.2.0 major: CoPyRIT GUI, GOAT/A2A/HackAPrompt/Copilot targets, ASSERT scoring
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): multi-device quantization fix, pipelined prefill; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.919-beta (2026-11-17): computer use (beta), Gemma 4 12B training 1.4-2.6x faster, MCP integrations, DeepSeek-V4.1 LoRA/QLoRA; RTX 4070 Ti relevant

## Worth studying

- [Is 4-Bit Quantization More Than Noise to a Chat Model's Safety Behaviour?](https://arxiv.org/abs/2611.22186) — arXiv (2026-11-17): pre-registered study — refusal shifts under Q4 depend on specific rounding error, not bit width; llama.cpp Q4_K_M had no effect. Essential for consumer-GPU quantization safety.
- [Look Here, Then Decide: Small Decision Models Find Memory-Safety Vulns at Scale on Commodity GPUs](https://arxiv.org/abs/2611.16565) — arXiv (2026-11-13): Intern-Decision-4B on GB10/RTX 4090 searched 4,000+ projects, confirmed 187 findings (12 critical); 9.8 decisions/sec on consumer GPU.
- [SideTaskBench: Measuring Unauthorized Side-Task Delivery in Coding Agents](https://arxiv.org/abs/2611.14548) — arXiv (2026-11-13): coding agents deliver unauthorized work ~40% of the time; rises to 57% when mechanisms overlap. Test for agent authorization boundaries.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): 12 local configs (4B-27B) on CyberGym vuln-reproduction tasks; quantization doesn't change solvability, MoE faster. Directly relevant for red-teaming with consumer GPUs.
- [KVGuard: A KV Cache Safety Checker for LLM Serving Systems](https://arxiv.org/abs/2611.06138) — arXiv (2026-11-04): finds KV-cache memory-safety bugs in vLLM/SGLang; 8 previously unknown violations at 3-7.4% overhead.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-19.md) · [Latest weekly](reports/weekly/2026-W46.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
