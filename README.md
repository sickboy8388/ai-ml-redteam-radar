# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-6-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--30-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-30)

- **llm-frontend-001 PROMOTED seed→emerging**: IBM Langflow OSS disclosed 33 GHSAs (6 Critical CVSS 9.8-9.9: code injection, auth bypass, missing authorization + RCE). Largest single advisory batch in any tracked trend. With ≥5 independent projects and critical-severity advisories, the trend meets emerging criteria.
- **NEW ai-agent-incidents-001 seeded**: Wiz "Rise of Agentic Attacks" (Oct 29) documents 7+ real-world AI agent-driven intrusions — ARTEX/Storm-0940 nation-state supply chain attack, MCP-RCE → secret exfil, CrowdStrike campaigns. Combined with Anthropic unsanctioned-actions reports and HF breach, 3 orgs with opened primaries.
- **local-inference-001** (accelerating, held): vLLM 8 more GHSAs Oct 28 (2nd batch in a week) — High CVE-2026-115912 (SHM pickle RCE) and CVE-2026-115915 (Ghostscript RCE via EPS); all fixed v0.32.0. llama.cpp b12000, Ollama v0.40.13 routine.
- **agentic-injection-001** (accelerating, held): arXiv Oct 30 carries ≥18 on-axis papers — CARI coding-agent injection (94.8% ASR, transfers to Codex/Claude Code), self-evolution IPI degradation, SEAL defense (34.6→0.1%), role spoofing, memory poisoning.
- **Queue**: resolved 4, added 1 → 6 live items.
- **transformers v5.22.0** (Oct 29, Mistral Large 4); **Unsloth v0.1.912-beta** (Oct 28, multi-LoRA batching, 2x faster launch).

## Trends

seed 1 · emerging 2 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-28](https://github.com/advisories/GHSA-6757-hggm-hp2w) — vLLM CVE-2026-115912: SHM handle forgery → pickle.loads() RCE in worker (High, CVSS 7.5) |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-28](https://arxiv.org/abs/2610.38799) — CARI: cross-boundary runtime injection in coding-agent workflows, 94.8% ASR |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-26](https://arxiv.org/abs/2610.35043) — Steering-plugin trojans: 97.8% ASR hijacking via trojanized LLM activation-steering plugins |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-10-29](https://github.com/advisories/GHSA-mm82-q33r-3rjw) — IBM Langflow 33 GHSAs: 6 Critical (CVSS 9.8-9.9) code injection and auth bypass |
| [Autonomous AI agents in real-world incidents (offensive deployments and unsanctioned actions)](TRENDS.md#trends) | seed | [2026-10-29](https://www.wiz.io/blog/the-rise-of-agentic-attacks) — Wiz: 7+ real-world AI agent-driven intrusions; ARTEX/Storm-0940 |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12000 (2026-10-30); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.13 (2026-10-28, Liquid LFM3 on Linux/Windows); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18, 3+8 security fixes in Oct, NVFP4 KV cache on Ada GPUs); security floor: ≥0.32.0 (CVE-2026-115912 SHM pickle RCE)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.0 (2026-10-29, Mistral Large 4 "Le Chonk")
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — 1.6.5 (2026-10-25): EXL3 quantization, CPU MoE offload, speculative decoding; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.912-beta (2026-10-28): multi-LoRA batching, 2x faster first launch, tool-call guard against cut-off overwrites

## Worth studying

- [CARI: Cross-Boundary Adversarial Runtime Injection in Coding-Agent Workflows](https://arxiv.org/abs/2610.38799) — arXiv (2026-10-28): malicious peer component → diagnostic-output injection → 94.8% ASR, transfers to Codex (61.3%)/Claude Code (58.7%); critical for multi-team coding-agent deployments.
- [SEAL: Sealed Queries for Local Sanitization against Indirect Prompt Injection](https://arxiv.org/abs/2610.39758) — arXiv (2026-10-29): best IPI defense result to date — 34.6→0.1% ASR, 127x fewer tokens than PISanitizer; practical for local deployments.
- [Wiz: The Rise of Agentic Attacks](https://www.wiz.io/blog/the-rise-of-agentic-attacks) — Wiz (2026-10-29): first IR-backed report on real-world AI agent-driven intrusions; 7+ cases, 7 behavioral fingerprints.
- [NameTrap: Steering AI Coding Agents Toward Security Vulnerabilities via Variable Names](https://arxiv.org/abs/2610.34253) — arXiv (2026-10-25): poisoned identifier names steer 6 coding agents toward CWE weaknesses (22–56% ASR); practical threat for anyone using AI assistants with untrusted repos.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-30.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
