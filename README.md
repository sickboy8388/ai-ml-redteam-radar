# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-2-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-7-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--11-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-11, daily)

- **llm-frontend-001** PROMOTED seed→emerging: NVD CVE-2026-97677 IBM Langflow arbitrary file write/read (CVSS 8.1); 5+ independent projects with advisories, confidence raised to high.
- **agentic-offensive-ops-001** PROMOTED seed→emerging: Sysdig documents JADEPUFFER autonomous-agent ransomware + HF breach attribution; BypassGym AI-agent EDR evasion benchmark; Shibboleth agentic-attacker fingerprinting. Now 5+ independent orgs.
- **local-inference-001** (accelerating, held): W46 demotion caveat CLEARED — LMDeploy CVE-2026-123818 SSRF (CVSS 7.5). llama.cpp b12274 adds FP8 KV-cache (axis 1b).
- **agentic-injection-001** (accelerating, held): StealthyPoison skill poisoning succeeds in Claude Code; SNAPRAG extracts 96.9% of RAG knowledge bases; 2nd impossibility theorem for agent gatekeeping. Paper velocity ≥10/week for 4+ weeks.
- **ai-supplychain-001** (emerging, held): LoRA backdoor defense failure paper → study_shelf. Approaching dormancy (15/21 days).
- **Queue**: 7 live (Gheist/GhostAction dropped). Two new 404 queued (Wiz AI Agent Eval, Sysdig AI agent risk).

## Trends

seed 0 · emerging 3 · accelerating 2 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-09](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-123818) — NVD: LMDeploy SSRF via URL parser differential (CVSS 7.5); W46 demotion caveat cleared |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-09](https://arxiv.org/abs/2611.12155) — StealthyPoison: procedural skill poisoning succeeds end-to-end in Claude Code workflow |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | emerging | [2026-10-27](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig: every ML pickle defense bypassed via parser differentials |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-08](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-97677) — NVD: IBM Langflow arbitrary file write/read (CVSS 8.1); promoted seed→emerging |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns](TRENDS.md#trends) | emerging | [2026-11-10](https://arxiv.org/abs/2611.13684) — BypassGym: AI agents evade real EDR products (17/18 success); promoted seed→emerging |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12283 (2026-11-11); b12274 adds **FP8 KV-cache support** (axis 1b, consumer-GPU relevant); security floor: ≥b9061 (CVE-2026-43631 UAF); note: 5 of 10 Cyera-disclosed bugs still unpatched
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.16 (2026-11-09, Ripple Preview, memory savings on Apple silicon); v0.40.17-rc0 pre-release (Nov 10); security floor: ≥0.35.0 (CVE-2026-103663 path traversal)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.33.0 (2026-11-02); security floor: ≥0.31.0 (CVE-2026-114053 code injection)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v4.12.1 (2026-10-23, security-only: SSRF hardening, redirect hop validation)
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.125.1 (2026-10-25); note: acquired by OpenAI (Mar 2026), open-source maintained
- **[transformers](https://github.com/huggingface/transformers)** — v5.22.1 (2026-10-30, Mistral Large 4 ~1T MoE, FP8 adapter training via PEFT)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.1.0 (2026-09-04); note: active at microsoft/PyRIT
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.6 (2026-10-31): greatly reduced VRAM during quantization, DeepseekV41 + Lfm3 support; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.916-beta (2026-11-06): Glass theme, browser windows, image/video gen; security note: expanded managed-account permissions for terminal/Python on macOS; RTX 4070 Ti relevant

## Worth studying

- [BypassGym: AI Agents vs Real EDR](https://arxiv.org/abs/2611.13684) — arXiv (2026-11-10): benchmark for AI agent EDR evasion; 5 model backends × 6 real EDR products × 3 payloads on Windows VMs; one model succeeded 17/18 runs. Directly relevant for red teamers evaluating agentic offense capabilities.
- [StealthyPoison: Procedural Skill Poisoning](https://arxiv.org/abs/2611.12155) — arXiv (2026-11-09): corrupts third-party LLM agent skills' decision-critical rules while maintaining advertised functionality; end-to-end success in Claude Code workflow. Critical read for anyone using agent skill ecosystems.
- [Suppression Is Not Erasure: LoRA Backdoor Defense Failure](https://arxiv.org/abs/2611.12807) — arXiv (2026-11-09): subspace-projection defenses reduce static ASR to 0% but 5-sample fine-tuning restores 100% ASR within 2 epochs. Essential caution for anyone pulling third-party LoRA adapters.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): 12 local configs (4B–27B) on CyberGym tasks; quantization doesn't change solvability, MoE faster. Directly relevant for red-teaming with consumer GPUs.
- [KVGuard: A KV Cache Safety Checker for LLM Serving Systems](https://arxiv.org/abs/2611.06138) — arXiv (2026-11-04): finds KV-cache memory-safety bugs in vLLM/SGLang; 8 previously unknown violations at 3–7.4% overhead.
- [Sysdig: three layers of open source defense for AI coding agents](https://www.sysdig.com/blog/three-layers-of-open-source-defense-for-ai-coding-agents-openshell-prempti-and-falco) — Sysdig (2026-10-27): OpenShell + Prempti + Falco layered defense blueprint for securing AI coding agents.
- [Sysdig: why every ML pickle defense is bypassed](https://www.sysdig.com/blog/in-a-pickle-why-every-pickle-defense-in-machine-learning-is-bypassed-the-same-way) — Sysdig Threat Research (2026-10-27): weights_only, safe_mode and scanners all fall to checker/loader differentials.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-11.md) · [Latest weekly](reports/weekly/2026-W45.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
