# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-9-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--13-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-13, daily)

- **agentic-offensive-ops-001** PROMOTED seed -> emerging: Microsoft "ARTEX abuse expands" (Nov 6) is the 2nd-org primary (after Wiz) documenting Storm-3358 using ARTEX against financial sector. Now 3 evidence items from 2 direct-primary orgs.
- **local-inference-001** (accelerating, held): W46 demotion caveat CLEARED — LMDeploy CVE-2026-123818 SSRF bypass (CVSS 7.5, Nov 9), llama.cpp b12340 SSRF fix (CORS proxy/media URLs reached private addresses, Nov 13), llama.cpp b12336 buffer overflow fix (Nov 13).
- **ai-supplychain-001** (emerging, held): Microsoft "Trained to betray" (Nov 12) — dataset poisoning (78% unsafe actions) and model poisoning (85.9-100% in-dist, 97% harness transfer to Claude Code) backdoor coding agents; in-the-wild poisoned rows found.
- **agentic-injection-001** (accelerating, held): arXiv Nov 10-11 carries 9+ on-axis papers; StealthyPoison (procedural skill poisoning, transfers across models) added to evidence.
- **llm-frontend-001** (seed, held): +1 Langflow advisory (CVE-2026-97677, path traversal, CVSS 8.1).
- **Queue**: 9 live; Gheist dropped. Study shelf: +2 (Microsoft sleeper agents, Say Shibboleth).

## Trends

seed 1 · emerging 2 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-13](https://github.com/advisories/GHSA-39wr-7q6h-cf68) — LMDeploy SSRF bypass (CVSS 7.5) + llama.cpp b12340 SSRF fix (CORS proxy reached private addresses) + b12336 buffer overflow fix |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-10](https://arxiv.org/abs/2611.12155) — StealthyPoison: procedural skill poisoning transfers across models, evades detectors; 20+ on-axis papers in 8 days |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-11-12](https://www.microsoft.com/en-us/security/blog/2026/11/12/trained-to-betray-how-post-training-supply-chain-attacks-hijack-coding-agents/) — Microsoft: dataset/model poisoning backdoors coding agents; 97% harness transfer to Claude Code; in-the-wild poisoned rows found |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns](TRENDS.md#trends) | emerging | [2026-11-06](https://www.microsoft.com/en-us/security/blog/2026/11/06/artex-abuse-expands-as-cybercriminals-target-financial-sector/) — Microsoft: Storm-3358 uses ARTEX against financial sector; 2nd-org primary after Wiz |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | seed | [2026-11-08](https://github.com/advisories/GHSA-54m9-hhxp-c88f) — IBM Langflow OSS CVE-2026-97677 (High, CVSS 8.1): path traversal file read/write |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12345 (2026-11-13); b12340 SSRF fix (CORS proxy + media URLs restricted to public addresses, PR #32115); b12336 buffer overflow fix (F64 tensor); security floor: >=b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.16 (2026-11-09, mmap Vulkan integrated GPUs, CUDA 13.5 ARM); v0.40.17-rc0 (Nov 10); security floor: >=0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02, /v1/decisions endpoint, watchdog stack dumps); security floor: >=0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.1 (2026-10-30, Mistral Large 4 ~1T MoE, FP8 adapter training via PEFT)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.6 (2026-10-31): greatly reduced VRAM during quantization, DeepseekV41 + Lfm3 support; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.917-beta (2026-11-11): INT8/FP8 image models on older NVIDIA cards, LTX-2.5 FP8 on 24GB, 2-8x faster generate on T4, FLUX VRAM reduction 36-43%; RTX 4070 Ti relevant

## Worth studying

- [Microsoft: Detecting sleeper agents hiding in AI model neurons](https://www.microsoft.com/en-us/security/blog/2026/11/10/detecting-sleeper-agents-hiding-in-ai-model-neurons/) — Microsoft Research (2026-11-10): <10 neuron edits backdoor agent models with inference-only compute; passes evals; detectable via weight diffing. Essential for anyone pulling open-weight checkpoints.
- [Say Shibboleth: Fingerprinting LLMs and Harnesses Behind Agentic Attacks](https://arxiv.org/abs/2611.12386) — arXiv (2026-11-10): shibboleth traps fingerprint attacker LLM + harness at ~90% accuracy; behavioral signals persist even when agents hide identity. Blue-team detection of agentic attackers.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): 12 local configs (4B-27B) on CyberGym vuln-reproduction tasks; quantization doesn't change solvability, MoE faster. Directly relevant for red-teaming with consumer GPUs.
- [KVGuard: A KV Cache Safety Checker for LLM Serving Systems](https://arxiv.org/abs/2611.06138) — arXiv (2026-11-04): finds KV-cache memory-safety bugs in vLLM/SGLang; 8 previously unknown violations at 3-7.4% overhead.
- [Sysdig: three layers of open source defense for AI coding agents](https://www.sysdig.com/blog/three-layers-of-open-source-defense-for-ai-coding-agents-openshell-prempti-and-falco) — Sysdig (2026-10-27): OpenShell + Prempti + Falco layered defense blueprint for securing AI coding agents.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
- [NameTrap: Steering AI Coding Agents Toward Security Vulnerabilities via Variable Names](https://arxiv.org/abs/2610.34253) — arXiv (2026-10-25): poisoned identifier names steer 6 coding agents toward CWE weaknesses (22-56% ASR); practical threat for anyone using AI assistants with untrusted repos.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-13.md) · [Latest weekly](reports/weekly/2026-W45.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
