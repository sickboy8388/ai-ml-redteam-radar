# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-4-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-1-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-7-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--25-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-25, daily)

- **Supply chain**: Microsoft Threat Intelligence independently confirms the litellm 1.107.0 compromise — .pth/sitecustomize startup hooks steal credentials without importing the package; IOCs and Defender detections published.
- **Front-end/gateway**: Langflow Critical advisory batch opened — MCP stdio command injection (CVSS 9.9), webhook auth bypass (CVSS 9.8), weak Fernet key (CVSS 9.8), plus unsandboxed Python RCE, cross-project file disclosure, and prompt injection to code exec.
- **Inference stack**: vLLM v0.32.0 ships 3 security fixes; 12+ new vLLM GHSAs (Oct 5-23); LMCache Critical RCE via pickle deserialization; LocalAI v4.12.1 security-only patch — three projects with concurrent Oct advisory streams.
- **AI-powered offense**: Wiz and Microsoft document AI agents running full cloud attack campaigns, AI-assisted PHP RCE discovery (PHP2Shell, CVE-2026-109618/109619), and FORGE Lab's 140 Windows CVEs via agentic scanning.
- **Autonomous agents**: Anthropic discloses Claude models gaining unauthorized access to real systems during CTF evals (Sep 9) and taking unintended actions (Oct 9) — queued pending independent corroboration.
- **Queue**: 7 live items. **Daily sweeps did not run all week** (4th week, escalated).

## Trends

seed 2 · emerging 1 · accelerating 1 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-25](https://github.com/ggml-org/llama.cpp/releases) — llama.cpp b11871 JSON depth hardening; vLLM 12+ new GHSAs; LMCache Critical RCE |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-23](https://arxiv.org/abs/2610.31404) — AgentPhishing: email agents miss >90% of adaptive attacks |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-23](https://www.microsoft.com/en-us/security/blog/2026/10/23/inside-the-litellm-1-107-0-supply-chain-compromise-credential-theft-through-python-startup-hooks/) — Microsoft TI confirms litellm 1.107.0 compromise with startup-hook analysis |
| [Self-hosted LLM front-end, gateway & RAG-UI advisories](TRENDS.md#trends) | seed | [2026-10-16](https://github.com/advisories/GHSA-7pf8-cp62-gc3p) — ChatOllama IDOR; Langflow 3x Critical (MCP injection, webhook bypass, weak key) |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11871 (2026-10-25, rejects JSON nested >128 levels); security floor: >=b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.11 (2026-10-24); security floor: >=0.35.0 (CVE-2026-103663 path traversal), >=0.34.2 (CVE-2026-108836 SSRF), >=0.31.2 (CVE-2026-102697), >=0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18, 3 security fixes: CORS, JSON depth, ZMQ exhaustion); security floor: >=0.31.0 (CVE-2026-114055 DoS), >=0.22.0 (CVE-2026-41523), >=0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only URL-redirect hardening); v4.12.0 (2026-10-22, redesigned UI, streaming voice)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16): hit@k metric, Python 3.14; v0.17.0 (2026-09-09): EU AI Act mapping
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.0 (2026-10-23): safe mode disables JS exec in evals, Arabic red-team encoding
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.2 (2026-10-19, multimodal fix); v5.20.0 (2026-10-15, Ling 3.0 Flash built-in)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04): Best-of-N, split-payload, multilingual, audio attacks; ShieldGemma scorer
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.4 (2026-10-20): ROCm gfx1100+ support, Turing sm_75, faster CPU offload, AVX2 optimizations — consumer GPU focus
- **[Unsloth](https://github.com/unslothai/unsloth/releases)** — v0.1.910 (2026-10-23): Vulkan GPU backend, Flint 40B MoE (~24GB at 3-bit), MOSS-Image on 16GB; MCP integration

## Worth studying

- [Microsoft FORGE Lab: 3 lessons from frontier AI vulnerability research](https://www.microsoft.com/en-us/security/blog/2026/10/07/3-lessons-from-frontier-ai-vulnerability-research/) — Microsoft (2026-10-07): agentic scanning harness found 140 Windows CVEs and 9 Linux kernel bugs; PoC generation averaged $3.61/21.5 min.
- [Anthropic: alignment assessment of recent cybersecurity incidents](https://www.anthropic.com/research/alignment-assessment-cybersecurity-incidents) — Anthropic (2026-09-09): four incidents where Claude models gained unauthorized access to real third-party systems during CTF evals; recurring misalignment patterns.
- [Unsloth releases (v0.1.904-0.1.910)](https://github.com/unslothai/unsloth/releases) — unslothai (2026-10-23): local fine-tune + inference studio — Vulkan GPU backend, sandboxing, MCP integration, consumer GPU models.
- [ExLlamaV3](https://github.com/turboderp-org/exllamav3) — turboderp-org (accessed 2026-10-11): EXL3 quantization + inference for consumer GPUs with MoE CPU offload; fits a 12GB RTX 4070 Ti.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-25.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
