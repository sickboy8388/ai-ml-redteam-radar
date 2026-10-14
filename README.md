# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-3-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-10-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--10--14-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-10-14, daily)

- **2 trends promoted to accelerating**: inference-server attack surface (2 new critical CVEs in one week — Ollama path-traversal RCE CVSS 9.4, llama.cpp UAF CVSS 9.2 — plus vLLM's 10 security fixes) and agentic prompt-injection (10 new arXiv papers in Oct 6–13, Agentjacking 85% success via Sentry MCP, PraisonAI 7 CVEs up to CVSS 10.0).
- **Supply-chain trend promoted seed→emerging**: HiddenLayer found fake OpenAI model on HuggingFace (244k downloads, infostealer payload); DPOison-VL achieves 98% alignment poisoning with 2% data.
- **25 new GHSA advisories** swept: Ollama path-traversal RCE, llama.cpp UAF, vLLM audio heap overflow, Flowise prompt-injection RCE, Langflow unsandboxed Python, PraisonAI cluster (7 CVEs), and more.
- **25 arXiv papers** verified: PackHallu (rule-file injection → package hallucination), CircuitBreak (safety-neuron pruning on Llama/Qwen), Kairos (AgentDojo attacks 47%→2.7%), TRAP/ATTCK-R jailbreak tools, DPOison-VL.
- **Vendor blogs opened** (first time): Microsoft Security Blog (FORGE Lab / MDASH, 140 Windows CVEs via AI), Wiz (AI SAST, Red Agent).
- **Tool releases**: llama.cpp b11609, Ollama v0.40.4 (MLX stable), vLLM v0.31.0 (10 security fixes), ExLlamaV3 v1.6.1 (ROCm, Turing, reduced VRAM), transformers v5.19.0, promptfoo 0.124.1, Unsloth v0.1.907.
- **Queue**: 10 live items; 3 resolved.

## Trends

seed 0 · emerging 1 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-08](https://github.com/advisories/GHSA-w8p2-phwr-px3r) — Ollama CVE-2026-103663: path traversal → RCE as root via /api/pull, CVSS 9.4 |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-10-13](https://arxiv.org/abs/2610.18457) — Kairos boundary monitor cuts AgentDojo attacks 47%→2.7%; 10 agent-security papers in one week |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-13](https://arxiv.org/abs/2610.18609) — DPOison-VL: 98% alignment poisoning with 2% data; fake OpenAI model hit #1 trending on HF |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b11609 (2026-10-14); b11608 fixed remotely-triggerable SIGSEGV DoS in llama-server; security floor: ≥b11393 (CVE-2026-107183 UAF)
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.4 (2026-10-12, decision models, MLX runner stable, multimodal embeddings); security floor: ≥0.35.0 (CVE-2026-103663 path-traversal RCE)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.31.0 (2026-10-05, 10 security fixes incl. multimodal kwargs injection prevention, prefix-cache isolation); security floor: ≥0.29.0 (CVE-2026-109311 audio heap overflow)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.11.0 (2026-10-02, audio scenes, path-confinement fixes)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.0 (2026-09-09): EU AI Act mapping, Python 3.13 support
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.124.1 (2026-10-08); 0.124.0 breaking changes (opt-in SDKs); security patches for Sharp/Codex SDK
- **[transformers](https://github.com/huggingface/transformers)** — v5.19.0 (2026-10-06, EmbeddingGemma2, expert-parallel token dispatch)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (Sep 4); Azure/PyRIT archived 2026-03-27 (moved here)
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.1 (2026-10-10): ROCm support, Turing (sm_75) optimization, reduced VRAM for drafting, hybrid drafting mode
- **[Unsloth](https://github.com/unslothai/unsloth)** — v0.1.907 (2026-10-13): LoRA+ support, layer offload, 3x faster MoE GGUFs, sandboxing, decision-model training

## Worth studying

- [Unsloth MoE Fine-Tuning Update](https://unslothai.substack.com/p/unsloth-2026-update-faster-moe) — Unsloth (2026-02-10): 12x faster MoE training, gpt-oss-20b fits 12.8GB VRAM (RTX 4070 Ti).
- [Analysis of LLMs Against Prompt Injection and Jailbreak Attacks](https://arxiv.org/abs/2602.22242) — arXiv (2026-02-24): inference-time defenses bypassed by long reasoning-heavy prompts on local models (Llama 3.2, Mistral, Qwen, Gemma).
- [ExLlamaV3 v1.6.1](https://github.com/turboderp-org/exllamav3/releases/tag/v1.6.1) — turboderp-org (2026-10-10): EXL3 quant + inference for consumer GPUs; ROCm, Turing, reduced VRAM for drafting.
- [HookPry: Attacker-Controlled Hook Updates Steer AI Agent Harnesses](https://arxiv.org/abs/2609.03884) — arXiv (2026-09-03): 92.5% compromise rate, 0% detection across 7 harnesses.
- [Cyera: Breaking Local AI Runtimes — 10 Vulnerabilities in llama.cpp](https://www.cyera.com/research/breaking-local-ai-runtimes-10-vulnerabilities-in-the-engine-behind-your-open-source-models) — Cyera (2026): 5 of 10 bugs unpatched — essential for local deployment hardening.

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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-10-14.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
