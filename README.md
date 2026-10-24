# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-4-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-5-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--24-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-24, daily sweep)

- **Two stage promotions**: inference-server and agentic-injection both move from emerging to **accelerating** — the first accelerating trends on this radar.
- **New seed trend**: `app-layer-001` — application-layer vulnerabilities in self-hosted LLM front-ends and gateways (Open WebUI 9 CVEs, ChatOllama IDOR, Langflow ownership bypass).
- **vLLM advisory explosion**: 8+ CVEs disclosed in Oct, including Critical code injection via `code_revision` (CVE-2026-114053, CVSS4 9.2) — arbitrary Python execution on unauthenticated `/tokenize` endpoint.
- **LocalAI Critical SSRF** (CVE-2026-114493, CVSS4 9.2): gallery URL redirect bypass reaches cloud metadata; v4.6.0–v4.11.0; fixed v4.12.1.
- **LMCache pickle RCE** (CVE-2026-105192, CVSS 9.8): unsafe deserialization in vLLM KV-cache layer; official containers run as root.
- **Open WebUI**: 9 CVEs in one batch (0.6.x–0.11.4), including session-cookie hijack via OAuth connections and terminal proxy privilege escalation.
- **Agentic**: 4 new independent papers (Agent Mosaic confidentiality leaks, AgentPhishing, MPIDetector, AgentTriage); now 12+ research groups.

## Trends

seed 2 · emerging 0 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | **accelerating** | [2026-10-23](https://github.com/advisories/GHSA-gx7p-2j49-hfq4) — vLLM 8+ CVEs incl. Critical code injection; LocalAI Critical SSRF; LMCache Critical pickle RCE |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | **accelerating** | [2026-10-22](https://arxiv.org/abs/2610.31404) — Agent Mosaic, AgentPhishing, MPIDetector, AgentTriage from 4 new independent groups |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-18](https://arxiv.org/abs/2610.21208) — LMCache pickle RCE bridges inference/supply-chain; support-persistent backdoors |
| [Self-hosted LLM front-end/gateway app-layer vulnerabilities (authz, priv esc, XSS, DoS)](TRENDS.md#trends) | seed | [2026-10-20](https://github.com/advisories/GHSA-qf42-fp6f-25w9) — Open WebUI 9 CVEs, ChatOllama IDOR, Langflow ownership bypass |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11851 (2026-10-24); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.10 (2026-10-23, Nemotron 3.5 Bolt E4B); v0.40.9 (Phonon speech, d3 decision models); v0.40.8 (Recursive Flint 40B MoE coding); security floor: ≥0.35.0 (CVE-2026-103663), ≥0.34.2 (CVE-2026-108836 SSRF), ≥0.31.2 (CVE-2026-102697), ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18, 3 security fixes + CORS hardening + /v1/systemone); security floor: **≥0.31.0** (CVE-2026-114053 code injection, CVE-2026-114055 DoS), ≥0.26.0 (CVE-2026-73560 SSRF), ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security: URL redirect hardening); v4.12.0 (decision routing, PII filtering, OAuth2 MCP); security floor: **≥v4.12.1** (CVE-2026-114493 SSRF)
- **[LMCache](https://github.com/LMCache/LMCache)** — security floor: **≥0.5.6** (CVE-2026-105192 pickle RCE); do not expose ZeroMQ port to untrusted networks
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16): hit@k metric, safe-token scoping, Python 3.14
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.0 (2026-10-23): safe mode disabling inline JS execution, Arabic encoding strategy
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.2 (2026-10-19, Muse Spark Open 816B, Beam coding model)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); no new release since last scan
- **[Unsloth](https://github.com/unslothai/unsloth)** — v0.1.910 (2026-10-23): REAP expert pruning (25–50% MoE experts), emSign compromised cert rejection, API key sandboxing, MoE GGUF 3x speedup; security hardening active
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — EXL3 quant + inference library for consumer GPUs, MoE CPU offload, TabbyAPI backend; speed claims unverified
- **[Open WebUI](https://github.com/open-webui/open-webui)** — security floor: **≥0.11.4** (9 CVEs: priv esc, session cookie hijack, XSS, DoS, info disclosure)

## Worth studying

- [vLLM v0.32.0 security advisory cluster](https://github.com/vllm-project/vllm/releases) — vLLM project (2026-10-18): 3 reviewed security fixes + CORS hardening + untrusted image restrictions. Essential upgrade from ≤0.31.x.
- [AgentTriage: Replayable Security Diagnosis Across Agent Runtimes](https://arxiv.org/abs/2610.30738) — arXiv (2026-10-22): deterministic security-event diagnosis across 5 agent runtimes; open-source tool for red-team post-exploitation analysis.
- [Unsloth releases (v0.1.906–0.1.910)](https://github.com/unslothai/unsloth/releases) — unslothai (2026-10-23): REAP expert pruning, security hardening, MoE GGUF speedups. Core axis-1b tool for the 12GB VRAM envelope.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): systematic audit of llama.cpp; 5 of 10 bugs unpatched — essential for anyone running llama.cpp or red-teaming local deployments.

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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-24.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
