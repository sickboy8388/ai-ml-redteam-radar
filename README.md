# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-1-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-0-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-5-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--08--24-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-08-24 — first run)

- **First SEED trend**: [Self-hosted inference server attack surface](#id-local-inference-001--self-hosted-inference-server-attack-surface-gguf-parsing--unauth-model-management-apis) — CVE cluster across Ollama (CVE-2026-7482 "Bleeding Llama"), llama.cpp (CVE-2026-27940 GGUF heap overflow, bypass of a prior fix), and Xinference (CVE-2026-61539, unsafe `eval()` on tool-call output → unauth RCE, CVSS 10.0, published 2026-08-21).
- **5 leads queued** (unverified): MCP tool-poisoning cluster, malicious Hugging Face models ("fake OpenAI privacy-filter", 244k downloads), Cyera exposure counts, ACM inference-time-defense bypass paper, NVIDIA Triton auth bypass.
- **Study picks**: garak v0.16.0 (Context Aware Scanning debut) + the MCP threat-modeling paper (arXiv 2603.22489).

## Trends

seed 1 · emerging 0 · accelerating 0 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing & unauth model-management APIs)](TRENDS.md#trends) | seed | [2026-08-21](https://github.com/advisories/GHSA-x2rj-828p-hx9m) — Xinference CVE-2026-61539, CVSS 10.0 |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b10604 (2026-08-24); security floor: ≥b8146 (CVE-2026-27940)
- **[Ollama](https://github.com/ollama/ollama)** — v0.32.15 (2026-08-19), v0.33.0-rc2 (2026-08-21); security floor: ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.27.1 (2026-08-11)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.9.0 (2026-08-20)
- **[garak](https://github.com/NVIDIA/garak)** — v0.16.0 (2026-08-04): technique/intent annotation, first Context Aware Scanning iteration (breaking config changes)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.122.0 (2026-08-04)
- **[transformers](https://github.com/huggingface/transformers)** — v5.15.1 (2026-08-19)
- **[PyRIT](https://github.com/Azure/PyRIT)** — no releases feed; track via tags

## Worth studying

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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-08-24.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
