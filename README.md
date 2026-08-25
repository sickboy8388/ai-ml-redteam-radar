# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-2-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-8-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--08--25-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-08-25)

- **New SEED trend**: [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory)](#trends) — promoted from the observation queue after 4 new independent primaries in one day: InjecMEM (agent memory injection), SkillBloat (malicious coding-agent skills, token amplification), plus two defensive frameworks (AgentFlow flow policies, AEGIS latent-manifold IPI detection).
- **llama.cpp v0.3.0** released today: first v0.3.x tag — dots3-note multimodal, MTP for GLM-4.5-Air, DeepSeek 4 tensor-split fixes, ggml v0.22.0.
- **Queue +3**: Hydra config-instantiation RCE (CVE-2026-68508, verified via GHSA), OWASP GenAI LLM Top 10 2026 (project page verified), vendor MCP-security writeups (re-queued after the cluster's promotion).
- **Blocker escalated**: session sandbox started empty — scheduled runs cannot re-clone the private GitHub repo without a persistent credential. See `TRENDS.md#blockers`.

## Trends

seed 2 · emerging 0 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing & unauth model-management APIs)](TRENDS.md#trends) | seed | [2026-08-21](https://github.com/advisories/GHSA-x2rj-828p-hx9m) — Xinference CVE-2026-61539, CVSS 10.0 |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory)](TRENDS.md#trends) | seed | [2026-08-24](https://arxiv.org/abs/2608.23471) — InjecMEM: one-interaction agent memory injection |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — v0.3.0 (2026-08-25, first v0.3.x tag); security floor: ≥b8146 (CVE-2026-27940)
- **[Ollama](https://github.com/ollama/ollama)** — v0.32.15 (2026-08-19), v0.33.0-rc3 (2026-08-21); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.27.1 (2026-08-11)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.9.0 (2026-08-20)
- **[garak](https://github.com/NVIDIA/garak)** — v0.16.0 (2026-08-04): technique/intent annotation, first Context Aware Scanning iteration (breaking config changes)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.122.0 (2026-08-04)
- **[transformers](https://github.com/huggingface/transformers)** — v5.15.1 (2026-08-19)
- **[PyRIT](https://github.com/Azure/PyRIT)** — no releases feed; tags API returned empty again (2nd run) — track via repo

## Worth studying

- [InjecMEM: Memory Injection Attack on LLM Agent Memory Systems](https://arxiv.org/abs/2608.23471) — arXiv (2026-08-24): agent memory is now a demonstrated injection target — one interaction poisons later retrieval-conditioned answers.
- [llama.cpp v0.3.0](https://github.com/ggml-org/llama.cpp/releases/tag/v0.3.0) — ggml-org (2026-08-25): the local-runtime baseline moved — new multimodal model support, MTP, ggml v0.22.0.
- [garak v0.16.0](https://github.com/NVIDIA/garak/releases/tag/v0.16.0) — NVIDIA (2026-08-04): the LLM vulnerability scanner moves from static probes toward intent-driven, context-aware evaluation.
- [MCP Threat Modeling & Tool Poisoning](https://arxiv.org/abs/2603.22489) — arXiv (2026-03-23): STRIDE/DREAD over the MCP stack; tool poisoning is the top client-side vuln; 5/7 major MCP clients lack static validation of tool descriptions.

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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-08-25.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
