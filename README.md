# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-11-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--07-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-07, daily)

- **agentic-offensive-ops-001** PROMOTED seed→emerging: Microsoft publishes 2 new ARTEX posts — Storm-3358 (Cambodia) targeting SE Asia financial sector (Nov 6), ARTEX agents scanning GitHub for exposed secrets with 5-min key-vault exfil (Nov 5). CrowdStrike documents 4 unreported actors using Claude Code/PentestGPT harnesses against healthcare, government, and global targets (Oct 21). Now ≥3 orgs with direct primaries opened.
- **llm-frontend-001** PROMOTED seed→emerging: 2 LiteLLM High advisories (Oct 27, GitHub Reviewed) discovered — arbitrary file read (GHSA-g5ff-637f-6q2m) and privilege escalation to proxy admin (GHSA-7hp6-4w63-5g45). Now ≥6 independent projects with advisories. Evidence 10/10.
- **ai-supplychain-001** (emerging, held): Microsoft Oct 30 Claude Code Cursor extension backdoor (SSH + cross-platform persistence, ~11h live) added to evidence. HF transformers v5.22.2 Jinja sandbox hardening noted.
- **agentic-injection-001** (accelerating, held): Multimodal-SEA benchmark (2611.08281) queued; paper velocity sustains.
- **local-inference-001** (accelerating, held): llama.cpp b12182 (Nov 7); b12177 crash fix invalid UTF-8, b12179 DMA overflow fix. No new CVEs.
- **Queue**: 11 live items (2 resolved, 5 added).

## Trends

seed 0 · emerging 3 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-10-28](https://github.com/advisories/GHSA-6757-hggm-hp2w) — vLLM High: forged SHM handle reaches pickle.loads; Oct 27-28 batch incl. code_revision RCE |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-05](https://arxiv.org/abs/2611.07640) — Task-tampering PI: observation/state-targeting attacks bypass defenses at 9.5–15.4% |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-30](https://www.microsoft.com/en-us/security/blog/2026/10/30/inside-malicious-claude-code-branded-cursor-extension-persistent-ssh-backdoor/) — Microsoft: malicious Claude Code Cursor extension with SSH backdoor; ~11h in marketplace |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-10-29](https://github.com/advisories/GHSA-mm82-q33r-3rjw) — IBM Langflow OSS: 25 GHSAs incl. 6 Critical (CVSS 9.8) RCE/auth-bypass; + 2 LiteLLM High |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns](TRENDS.md#trends) | emerging | [2026-11-06](https://www.microsoft.com/en-us/security/blog/2026/11/06/artex-abuse-expands-as-cybercriminals-target-financial-sector/) — Microsoft: Storm-3358 uses ARTEX against financial sector; CrowdStrike: 4 actors with Claude Code harnesses |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12182 (2026-11-07); b12177 crash fix (invalid UTF-8), b12179 DMA overflow/div-by-zero fixes; security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.15 (2026-11-03, Kimi Code CLI, YaRN Qwen3/3.5); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02, /v1/decisions endpoint, watchdog stack dumps); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25)
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.2 (2026-11-06, Jinja sandbox hardening PR #50431, distributed fixes)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.6 (2026-10-31): greatly reduced VRAM during quantization, DeepseekV41 + Lfm3 support; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.916-beta (2026-11-06): two-GPU image/video, LTX-2.5 on 16-24GB GPUs, faster model loads/generation; RTX 4070 Ti relevant

## Worth studying

- [CrowdStrike: Agentic AI Campaigns — 4 Threat Actors Using Claude Code](https://www.crowdstrike.com/en-us/blog/crowdstrike-uncovers-new-agentic-ai-campaigns/) — CrowdStrike (2026-10-21): 4 unreported actors with Claude Code/PentestGPT harnesses; healthcare/govt/global targets in 4+ countries. Essential for understanding real-world agentic offense.
- [Microsoft: Malicious Claude Code-branded Cursor Extension](https://www.microsoft.com/en-us/security/blog/2026/10/30/inside-malicious-claude-code-branded-cursor-extension-persistent-ssh-backdoor/) — Microsoft (2026-10-30): tampered extension with SSH backdoor + cross-platform persistence; essential for AI coding extension users.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): 12 local configs (4B–27B) on CyberGym vuln-reproduction tasks; quantization doesn't change solvability, MoE faster. Directly relevant for red-teaming with consumer GPUs.
- [KVGuard: A KV Cache Safety Checker for LLM Serving Systems](https://arxiv.org/abs/2611.06138) — arXiv (2026-11-04): finds KV-cache memory-safety bugs in vLLM/SGLang; 8 previously unknown violations at 3–7.4% overhead.
- [Sysdig: three layers of open source defense for AI coding agents](https://www.sysdig.com/blog/three-layers-of-open-source-defense-for-ai-coding-agents-openshell-prempti-and-falco) — Sysdig (2026-10-27): OpenShell + Prempti + Falco layered defense blueprint for securing AI coding agents.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-07.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
