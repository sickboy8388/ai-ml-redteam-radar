# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-10-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--08-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-08, daily 2nd pass)

- **ai-supplychain-001** (emerging, held): +1 evidence — transformers v5.22.2 Jinja sandbox hardening patches CPython dict exploit and older Jinja escape in chat-template rendering; affects vLLM/transformers. Unsloth v0.1.916-beta enforces safetensors-only for NVFP4 diffusion.
- **agentic-offensive-ops-001** (seed, held): +1 evidence — Sysdig 555 Benchmark independently documents JADEPUFFER agentic ransomware and confirms HF breach was OpenAI eval. Now 2 orgs (Wiz + Sysdig); needs 3rd for emerging.
- **local-inference-001** (accelerating, held): llama.cpp b12192–b12201 routine dev (UTF-8 sanitization, VRAM bounds check). NVD 0 new CVEs.
- **agentic-injection-001** (accelerating, held), **llm-frontend-001** (seed, held).
- **Queue**: +4 items (Multimodal-SEA, SimBreak, TraceMRT, OWASP LLM Top 10 2026); 10 live.

## Trends

seed 2 · emerging 1 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-30](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-119706) — NVD: LMDeploy unauth pickle RCE (CVSS 9.3) + LM Studio path traversal (8.7); with vLLM Oct 27-28 batch incl. code_revision RCE |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-05](https://arxiv.org/abs/2611.07640) — Task-tampering PI: observation/state-targeting attacks bypass defenses at 9.5–15.4% |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-11-06](https://github.com/huggingface/transformers/releases/tag/v5.22.2) — transformers v5.22.2: Jinja sandbox hardening patches CPython dict exploit + older escape; min Jinja 3.1.6 |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | seed | [2026-10-29](https://github.com/advisories/GHSA-mm82-q33r-3rjw) — IBM Langflow OSS: 25 GHSAs incl. 6 Critical (CVSS 9.8) RCE/auth-bypass |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns](TRENDS.md#trends) | seed | [2026-11-05](https://www.sysdig.com/blog/refreshing-the-555-benchmark-for-cloud-detection-and-response-in-the-ai-era) — Sysdig: JADEPUFFER agentic ransomware + HF breach confirmed as OpenAI eval; 2nd-org corroboration |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12201 (2026-11-08); b12199 sanitizes invalid UTF-8 in PEG tool-call args; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.15 (2026-11-03, Kimi Code CLI, YaRN Qwen3/3.5); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02, /v1/decisions endpoint, watchdog stack dumps); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.2 (2026-11-06, security patch: Jinja sandbox hardening, distributed NCCL fix)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.6 (2026-10-31): greatly reduced VRAM during quantization, DeepseekV41 + Lfm3 support; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.916-beta (2026-11-06): safetensors-only NVFP4 diffusion loading (security hardening), CUDA graph decoding default for Llama/Qwen, two-GPU generation; RTX 4070 Ti relevant

## Worth studying

- [HuggingFace transformers v5.22.2 — Jinja sandbox hardening](https://github.com/huggingface/transformers/releases/tag/v5.22.2) — HuggingFace (2026-11-06): patches CPython dict exploit and older Jinja escape in chat-template rendering; minimum Jinja 3.1.6. Update if running vLLM or transformers locally.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): 12 local configs (4B–27B) on CyberGym vuln-reproduction tasks; quantization doesn't change solvability, MoE faster. Directly relevant for red-teaming with consumer GPUs.
- [KVGuard: A KV Cache Safety Checker for LLM Serving Systems](https://arxiv.org/abs/2611.06138) — arXiv (2026-11-04): finds KV-cache memory-safety bugs in vLLM/SGLang; 8 previously unknown violations at 3–7.4% overhead.
- [Sysdig: three layers of open source defense for AI coding agents](https://www.sysdig.com/blog/three-layers-of-open-source-defense-for-ai-coding-agents-openshell-prempti-and-falco) — Sysdig (2026-10-27): OpenShell + Prempti + Falco layered defense blueprint for securing AI coding agents.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
- [NameTrap: Steering AI Coding Agents Toward Security Vulnerabilities via Variable Names](https://arxiv.org/abs/2610.34253) — arXiv (2026-10-25): poisoned identifier names steer 6 coding agents toward CWE weaknesses (22–56% ASR); practical threat for anyone using AI assistants with untrusted repos.
- [SCS: Supply-Chain Scanner for Agent Skills](https://arxiv.org/abs/2610.33489) — arXiv (2026-10-24): program analysis finds 627 confirmed malicious skills in 66k ClawHub skills. First large-scale automated detection.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-08.md) · [Latest weekly](reports/weekly/2026-W45.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
