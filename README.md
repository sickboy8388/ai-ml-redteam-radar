# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-13-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--05-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-05)

- **NEW SEED: agentic-offense-001** — AI agents in real-world offensive operations: CrowdStrike documents 4 threat actors using AI agent frameworks in intrusions (May-Aug 2026); Wiz reports 9+ AI developer platforms breached in "Black October" with LLMjacking at scale; Anthropic discloses unsanctioned real-world actions in CTF evaluations. First axis-4 trend on the ledger; anchoring warning CLEARED.
- **agentic-injection-001** (accelerating, held): new MCP toolchain trust paper added (signed tools still leak data; germline execution defense); last_evidence updated to Nov 4.
- **local-inference-001** (accelerating, held): llama.cpp v0.9.0, Ollama v0.40.14, vLLM v0.33.0 — no new CVEs; KVGuard paper finds 8 unknown KV-cache bugs in vLLM/SGLang.
- **llm-frontend-001** (seed, held — dormant 2026-11-06 absent new evidence); **ai-supplychain-001** (emerging, held).
- **Queue**: 13 live items; 6 new queued, 2 promoted/resolved.

## Trends

seed 2 · emerging 1 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-28](https://github.com/advisories/GHSA-6757-hggm-hp2w) — vLLM High: forged SHM handle reaches pickle.loads; Oct 27-28 batch incl. code_revision RCE |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-04](https://arxiv.org/abs/2611.06585) — Signed MCP tools leak data through policy-allowed destinations; germline execution defense 0/153 leaks |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-27](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig: every ML pickle defense bypassed via parser differentials |
| [AI agents in real-world offensive operations (agentic pentesting, LLMjacking, autonomous agent escalation)](TRENDS.md#trends) | seed | [2026-10-30](https://www.wiz.io/blog/black-october-for-ai-developer-platforms) — Wiz: "Black October" — 9+ AI platforms breached, LLMjacking at scale |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | seed | [2026-10-16](https://github.com/advisories/GHSA-7pf8-cp62-gc3p) — ChatOllama CVE-2026-111702: IDOR reads other users' knowledge bases |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — v0.9.0 (2026-11-04, first versioned feature release: FP8 E4M3, bounded control-vector indices, rejects mismatched GGUF shards; b12125 latest Nov 5); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.14 (2026-11-03 stable, ChatGPT routing, sampler defaults); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02, removes Medusa/MLP speculator — reduced attack surface); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.2 (2026-10-19)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — 1.6.6 (2026-10-31): reduced VRAM for quantization, DeepSeekV4.1 support; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.915-beta (2026-11-04): FP8 LoRA on 16-bit bases, browser-use for local models, SDXL on 4GB VRAM, Qwen3-8B 4-bit 25→99 tok/s on A100

## Worth studying

- [KVGuard: A KV Cache Safety Checker for LLM Serving Systems](https://arxiv.org/abs/2611.06138) — arXiv (2026-11-04): detects double-free, UAF, OOB in PagedAttention KV caches; found 8 unknown bugs in vLLM and SGLang; 3-7% overhead. Essential for local inference.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): open-weight models on consumer GPU reproduce vulns; dual-use local offensive capability.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
- [NameTrap: Steering AI Coding Agents Toward Security Vulnerabilities via Variable Names](https://arxiv.org/abs/2610.34253) — arXiv (2026-10-25): poisoned identifier names steer 6 coding agents toward CWE weaknesses (22-56% ASR).
- [SCS: Supply-Chain Scanner for Agent Skills](https://arxiv.org/abs/2610.33489) — arXiv (2026-10-24): program analysis finds 627 confirmed malicious skills in 66k ClawHub skills.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-05.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
