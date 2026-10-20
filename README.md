# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-4-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-1-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-5-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--20-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-20)

- **agentic-injection-001 promoted emerging→accelerating**: SEAL demonstrates persistent tool poisoning across multi-round agent workflows; PIAtlas provides the first mechanism-based prompt injection taxonomy + largest license-clean dataset; three independent defensive papers (SpanGuard, Connection Escrow, CoordGuard) signal field maturation. 10+ independent groups, active CVEs, offensive+defensive research at volume.
- **New SEED trend app-layer-001**: Self-hosted LLM front-end/gateway app-layer attack surface — Open WebUI disclosed 15+ CVEs in one batch (fixed 0.11.4), IBM Langflow has RCE + message-ownership bypass, ChatOllama has unauthenticated knowledge-base IDOR, Portkey AI Gateway has SSRF reaching loopback/Docker. ≥4 independent projects.
- **ai-supplychain-001**: RAGLeak adds supply-chain privacy backdoors in RAG components (survives fine-tuning, up to 100% ASR).
- **local-inference-001**: held at emerging (10/10 evidence); Ollama SSRF CVE-2026-108836 verified, vLLM v0.32.0 ships CORS hardening.
- **Queue**: 5 live items; app-layer advisories promoted, Ollama SSRF resolved.

## Trends

seed 2 · emerging 1 · accelerating 1 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | **accelerating** | [2026-10-20](https://arxiv.org/abs/2610.25372) — SEAL: persistent tool poisoning via universal prefix-eliciting triggers across multi-round workflows |
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | emerging | [2026-10-08](https://github.com/advisories/GHSA-w8p2-phwr-px3r) — Ollama /api/pull path traversal, CVSS4 9.4, unauth |
| [Self-hosted LLM front-end/gateway app-layer attack surface (auth bypass, XSS, SSRF, privilege escalation)](TRENDS.md#trends) | seed | [2026-10-20](https://github.com/advisories/GHSA-qf42-fp6f-25w9) — Open WebUI 15+ CVEs, Langflow RCE, ChatOllama IDOR, Portkey SSRF |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | seed | [2026-10-19](https://arxiv.org/abs/2610.25937) — RAGLeak: supply-chain privacy backdoors in RAG survive fine-tuning |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11751 (2026-10-20); b11744 adds `--connect` P2P server access beyond LAN (review before enabling); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.7-rc0 (2026-10-18, pre-release; spec decoding, Responses API reasoning); v0.40.6 (2026-10-16 stable); security floor: ≥0.35.0 (CVE-2026-103663 path traversal), ≥0.34.2 (CVE-2026-108836 SSRF), ≥0.31.2 (CVE-2026-102697), ≥0.17.1 (CVE-2026-7482)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.32.0 (2026-10-18): NVFP4 KV cache on more GPU generations, Model Runner V2 default on ROCm, GPU n-gram speculator, CORS hardening, untrusted-image restrictions, JSON depth limit; security floor: ≥0.22.0 (CVE-2026-41523), ≥0.14.1 (CVE-2026-22778)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, decision models, signed OCI galleries)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16): hit@k attack success rate metric, Python 3.14 support, detector/probe fixes
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08): OpenAI Decisions support, Claude Opus 5.5/Sonnet 5.5/GPT-6 models; 0.124.0 breaking: hosted ChatKit removed, integrations made opt-in
- **[transformers](https://github.com/huggingface/transformers)** — v5.20.2 (2026-10-19): EmbeddingGemma2, Beam (coding/agentic), FSDP×TP checkpoints, expert-parallel dispatch; quantization during export
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); no new release
- **[Unsloth](https://github.com/unslothai/unsloth/releases)** — v0.1.909-beta (2026-10-19): DeepSeek-V4.1-Flash local, Vulkan for non-NVIDIA GPUs, MCP for coding agents (`unsloth mcp add`), multi-GPU FSDP2 alpha, LoRA training perf improvements
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — EXL3 quant + inference library for consumer GPUs, MoE CPU offload, TabbyAPI backend; speed claims unverified
- **[Open WebUI](https://github.com/open-webui/open-webui)** — **upgrade to ≥0.11.4** (15+ CVEs fixed in one batch: privesc, session theft, XSS, DoS, authz bypass)

## Worth studying

- [SEAL: Persistent Tool Poisoning Attack against LLM Agents](https://arxiv.org/abs/2610.25372) — Zhou et al. (2026-10-18): single-round tool-poisoning evaluations overstate defenses; universal triggers sustain attack across multi-round agent workflows.
- [PIAtlas: Decomposing the Unbounded Prompt Injection Attack Space](https://arxiv.org/abs/2610.24999) — Damianakis & Psounis (2026-10-18): first mechanism-based PI taxonomy + PICorpus; maps coverage gaps in agent benchmarks.
- [Unsloth releases (v0.1.904–0.1.909)](https://github.com/unslothai/unsloth/releases) — unslothai (2026-10-19): local fine-tune + inference studio — Vulkan, MCP, DeepSeek-V4.1-Flash local, FSDP2 alpha.
- [ExLlamaV3](https://github.com/turboderp-org/exllamav3) — turboderp-org (accessed 2026-10-11): EXL3 quantization + inference for consumer GPUs with MoE CPU offload; fits a 12GB RTX 4070 Ti.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-20.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
