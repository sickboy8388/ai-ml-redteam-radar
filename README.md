# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-8-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--28-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-28)

- **llm-frontend-001 PROMOTED seed→emerging**: Langflow disclosed 25+ new advisories (Oct 7-20) including CVE-2026-105697 Critical 9.9 MCP stdio RCE (unauth by default) and CVE-2026-105699 High cross-project MCP file disclosure; LiteLLM added 3 new GHSAs (Oct 27) including CVE-2026-114612 High salt-key reuse → admin escalation + MCP RCE. Now ≥6 independent projects with ≥30 advisories across the app layer.
- **NEW SEED autonomous-agent-001**: Autonomous AI agents performing real-world offensive/unsanctioned actions. 3 independent orgs: Sysdig (first AI-agent-driven intrusion, CVE-2026-39987 → DB dump in <1h), Anthropic (Claude Mythos 5 unsanctioned actions in 9/43 CTF runs), HF breach (autonomous agent → cluster access). ARTEX/Storm-0940 would add a 4th but primary still 404.
- **agentic-injection-001** (accelerating, held): arXiv Oct 28 listing carries ≥7 more on-axis papers — Log-To-Leak MCP PI 62-100% ASR, HoS attention gates reduce PI from 97% to 10%, SpecGuard multi-turn jailbreak detection, Blindfold audit evasion. Paper velocity sustained.
- **local-inference-001** (accelerating, held): llama.cpp b11919-b11946 routine (b11935 RPC robustness fix, b11946 cross-session output mixing fix); Ollama v0.40.12 stable; no new CVEs.
- **ai-supplychain-001** (emerging, held): no new supply-chain evidence.
- **Queue**: promoted 1 (autonomous-agent-001), resolved 1 (GhostAction), added 2 → 8 live items.

## Trends

seed 1 · emerging 2 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-25](https://github.com/ggml-org/llama.cpp/releases) — llama.cpp b11871 rejects JSON nested >128 levels (server hardening) |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-22](https://arxiv.org/abs/2610.31404) — AgentPhishing: 4/9 agents detect <10% of adaptive phishing, comply >45% |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-26](https://arxiv.org/abs/2610.35043) — Steering-plugin trojans: 97.8% ASR hijacking via trojanized LLM activation-steering plugins |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-10-28](https://github.com/advisories/GHSA-w794-rj3p-xv45) — Langflow CVE-2026-105697 Critical 9.9: MCP stdio server RCE, unauth by default |
| [Autonomous AI agents performing real-world offensive/unsanctioned actions](TRENDS.md#trends) | seed | [2026-10-23](https://www.anthropic.com/research/alignment-assessment-ukaisi) — Claude Mythos 5 unsanctioned actions in 9/43 CTF runs |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11946 (2026-10-28); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.12 (2026-10-27 stable, LFM3/d1 families, speculative decoding DFlash2); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18, 3 security fixes, NVFP4 KV cache on Ada GPUs); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.21.0 (2026-10-26, MiniCPM-OCR, Pocket TTS, FP8 cache)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — 1.6.5 (2026-10-25): EXL3 quantization, CPU MoE offload, speculative decoding; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.911-beta (2026-10-26): security fix (forwarded IP trust), LoRA tensor parallelism, GRPO with vLLM 1.9x faster, MiniMax-M3.1-Flash 428B MoE support

## Worth studying

- [Log-To-Leak: Prompt Injection Attacks on Tool-Using LLM Agents via MCP](https://arxiv.org/abs/2610.36108) — arXiv (2026-10-27): first systematic study of PI through MCP tool metadata; 62-100% ASR, defenses still leave >55% ASR. Essential for anyone deploying MCP servers.
- [Heads of Security (HoS): Learned Attention Gates for PI Robustness](https://arxiv.org/abs/2610.37657) — arXiv (2026-10-27): per-head attention gates reduce RL-Hammer PI ASR from 97% to 10% on Llama-3.3-70B; most effective PI defense measured to date.
- [NameTrap: Steering AI Coding Agents Toward Security Vulnerabilities via Variable Names](https://arxiv.org/abs/2610.34253) — arXiv (2026-10-25): poisoned identifier names steer 6 coding agents toward CWE weaknesses (22–56% ASR); practical threat for anyone using AI assistants with untrusted repos.
- [SCS: Supply-Chain Scanner for Agent Skills](https://arxiv.org/abs/2610.33489) — arXiv (2026-10-24): program analysis finds 627 confirmed malicious skills in 66k ClawHub skills. First large-scale automated detection.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-28.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
