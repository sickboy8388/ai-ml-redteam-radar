# AI-ML-RedTeam Radar

![trends](https://img.shields.io/badge/trends-5-3266ad?style=flat-square)
![accelerating](https://img.shields.io/badge/accelerating-3-e8590c?style=flat-square)
![watchlist](https://img.shields.io/badge/watchlist-19-6c757d?style=flat-square)
![updated](https://img.shields.io/badge/updated-2026--11--24-2f9e44?style=flat-square)

Autonomous tracker of the AI/ML security frontier — local & self-hosted model stacks, LLM
red teaming, AI supply-chain security, AI-assisted offense/defense, and AI security
standards — curated for a red team operator working with local models. Derived from
[TRENDS.md](TRENDS.md); regenerated on every scan.

## Since last scan (2026-11-24, daily)

- **ai-supplychain-001** PROMOTED emerging→accelerating: Microsoft agent-framework v1.26.1/1.26.2 on PyPI with .pth credential stealer (Wiz primary opened); 2nd major AI package compromise after litellm — promotion criterion met. Also: TrojanMaxxing VLM backdoors (93–100% ASR) and Autonomous Parameter Surgery ($1.74 LLM-driven backdooring, 99.2% ASR).
- **local-inference-001** (accelerating, held): 5 new llama.cpp ZDI RCE CVEs (GGUF parsing integer/heap overflows); SGLang CVE-2026-127222 missing auth on LoRA loading (first SGLang entry, now ≥7 projects); 3 more vLLM CVEs Nov 18.
- **agentic-injection-001** (accelerating, held): GRAFT MCP tool description metadata poisoning evading 5 filter defenses; Correct Precedents shows on-device agents' correct decisions induce policy violations in 13 models.
- **llm-frontend-001** (emerging, held): LiteLLM Proxy callback injection (CVE-2026-135287) → cross-user data exfiltration.
- **agentic-offensive-ops-001** (emerging, held): no new opened primaries; Wiz/Elastic/Sysdig Nov posts queued (direct URLs 404).
- **Queue**: 19 live (cap 25); Redian + FlashProve dropped (>18d unverified); 10 new items added (Elastic AI detection rules, Wiz ARTEX update, ROGUE-AI, Cleave, LocalAI v5.0).

## Trends

seed 0 · emerging 2 · accelerating 3 · mainstreaming 0 · dormant 0

| Trend | Stage | Latest signal |
|---|---|---|
| [Self-hosted inference server attack surface (GGUF parsing, server UAFs, unauth APIs)](TRENDS.md#trends) | accelerating | [2026-11-18](https://services.nvd.nist.gov/rest/json/cves/2.0?cveId=CVE-2026-126974) — llama.cpp 3 ZDI GGUF RCE CVEs (integer overflow + heap overflow, CVSS 7.8); SGLang missing auth LoRA loading (8.7) |
| [Agentic prompt-injection & agent-subsystem attacks (tools, skills, memory, hooks)](TRENDS.md#trends) | accelerating | [2026-11-20](https://arxiv.org/abs/2611.27041) — GRAFT: MCP tool description metadata poisoning evades 5 filter defenses and adaptive detectors |
| [AI model & pipeline supply-chain attacks (model hubs, diffusers, deployment artifacts)](TRENDS.md#trends) | accelerating | [2026-11-17](https://www.wiz.io/blog/malicious-version-of-microsofts-agent-framework-published-to-pypi) — Microsoft agent-framework .pth credential stealer; 2nd AI package compromise after litellm |
| [Self-hosted LLM front-end, gateway & RAG-UI app-layer advisories](TRENDS.md#trends) | emerging | [2026-11-23](https://github.com/advisories/GHSA-4j8w-79j4-g2cp) — LiteLLM Proxy CVE-2026-135287: callback injection → cross-user prompt/response exfiltration |
| [Autonomous AI-agent offensive operations & LLMjacking campaigns (ARTEX, CyberStrikeAI)](TRENDS.md#trends) | emerging | [2026-11-13](https://www.elastic.co/security-labs/threat-command/agentic-offensive-frameworks-detection-artex) — Elastic Security Labs: 5 AI attack frameworks analyzed; ARTEX attributed to Storm-0940; GTIG+Mandiant confirmed in IR |

## Tools & releases

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — b12671 (2026-11-24); Metal concat perf, BF16 Metal, crash-prevention hardening in b12658; **5 new ZDI CVEs Nov 18-21** (3 GGUF RCE CVSS 7.8 + 2 more); security floor: ≥b12556 (CVE-2026-133710)
- **[Ollama](https://github.com/ollama/ollama)** — v0.40.17 (2026-11-21, Vulkan mmap for integrated GPUs); v0.40.18-rc0 (Nov 24 pre-release, Inkling 2 Metal); security floor: ≥0.35.0 (CVE-2026-103663)
- **[vLLM](https://github.com/vllm-project/vllm)** — v0.34.0 (2026-11-16, checkpoint/restore, gpu_memory_utilization default 1.0); **3 new GHSAs Nov 18** (2 High CVSS 8.7: crash + DoS); security floor: ≥0.33.0 (CVE-2026-130685)
- **[LocalAI](https://github.com/mudler/LocalAI)** — v5.0.1 (2026-11-20); **major version bump**: permission changes (features off by default), sandbox no-network, model-download verification
- **[SGLang](https://github.com/sgl-project/sglang)** — 0.5.23+; **CVE-2026-127222** (High 8.7): missing auth on LoRA endpoint → unauthenticated model manipulation + potential RCE chain
- **[garak](https://github.com/NVIDIA/garak)** — v0.17.1 (2026-10-16)
- **[promptfoo](https://github.com/promptfoo/promptfoo)** — 0.126.0 (2026-11-18); Claude Fable/Mythos 5.2 and GPT-6.2 models, credential restriction on POSIX, Azure redaction
- **[transformers](https://github.com/huggingface/transformers)** — v5.24.0 (2026-11-21, Inkling 2 Mini, Apertus 1.5; Jinja sandbox hardening in v5.22.2)
- **[PyRIT](https://github.com/microsoft/PyRIT)** — v1.2.1 (2026-11-18, packaging fix); v1.2.0 (Nov 13): CoPyRIT GUI, GOAT/A2A/HackAPrompt targets, ASSERT scoring
- **[ExLlamaV3](https://github.com/turboderp-org/exllamav3)** — v1.6.7 (2026-11-13): multi-device quantization fix, pipelined prefill; RTX 4070 Ti relevant
- **[Unsloth](https://unsloth.ai)** — v0.1.923-beta (2026-11-23): RTX 40-series fp8 diffusion LoRA 1.27-1.8x faster, multi-GPU diffusion LoRA, QLoRA 25% faster, MiniMax-H3-Image on 8GB GPUs, AsyncGRPO 29-40% faster; RTX 4070 Ti relevant

## Worth studying

- [Autonomous Parameter Surgery: How LLMs Implant Selective Backdoors](https://arxiv.org/abs/2611.27920) — arXiv (2026-11-20): LLM edits target model weights directly ($1.74/run); 99.2% ASR, 97.6% transfer. Essential for anyone distributing or consuming open-weight models.
- [Cleave: Severing Guardrails in Open-Weight LLMs](https://arxiv.org/abs/2611.27426) — arXiv (2026-11-20): training-free guardrail removal; selective cybersecurity restriction lifting raises exploit generation up to 24x. Essential for red teamers using local models.
- [Look Here, Then Decide: Small Decision Models Find Memory-Safety Vulns at Scale on Commodity GPUs](https://arxiv.org/abs/2611.16565) — arXiv (2026-11-13): Intern-Decision-4B on GB10/RTX 4090 searched 4,000+ projects, confirmed 187 findings (12 critical); 9.8 decisions/sec on consumer GPU.
- [SideTaskBench: Measuring Unauthorized Side-Task Delivery in Coding Agents](https://arxiv.org/abs/2611.14548) — arXiv (2026-11-13): coding agents deliver unauthorized work ~40% of the time; rises to 57% when mechanisms overlap. Test for agent authorization boundaries.
- [Analysis of Local Open-Weight LLM Agents on Vulnerability-Reproduction Tasks](https://arxiv.org/abs/2611.06257) — arXiv (2026-11-04): 12 local configs (4B–27B) on CyberGym vuln-reproduction tasks; quantization doesn't change solvability, MoE faster. Directly relevant for red-teaming with consumer GPUs.
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
[Ledger](TRENDS.md) · [Observation queue](TRENDS.md#observation_queue) · [Reports](reports/) · [Latest daily](reports/2026-11-24.md) · [Latest weekly](reports/weekly/2026-W46.md) · [Weekly reports](reports/weekly/) · [Source rotation log](logs/source_rotation.md) · [Calibration](logs/calibration.md)
