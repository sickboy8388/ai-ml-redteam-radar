# Source rotation log

Append-only. One dated entry per run: which sources were `opened` or `degraded: <reason>`.

## 2026-08-24 (first run)
- opened: tool repos & releases via GitHub API — llama.cpp (b10604, 2026-08-24), Ollama
  (v0.32.15 stable / v0.33.0-rc2, 2026-08-21), vLLM (v0.27.1, 2026-08-11), LocalAI
  (v4.9.0, 2026-08-20), garak (v0.16.0, 2026-08-04, opened full release notes), promptfoo
  (0.122.0, 2026-08-04), transformers (v5.15.1, 2026-08-19). PyRIT: no releases feed
  (tags-based distribution — track via tags in future runs).
- opened: GHSA — ecosystem sweep + full advisories GHSA-x2rj-828p-hx9m (Xinference,
  CVE-2026-61539), GHSA-x8qc-fggm-mpqg (Ollama, CVE-2026-7482),
  GHSA-3p4r-fq3f-q74v (llama.cpp, CVE-2026-27940).
- opened: papers — arXiv abs/2603.22489 (MCP tool poisoning threat modeling).
- degraded: r/LocalLLaMA JSON endpoint (reddit.com) — request rejected this session.
- degraded: vendor blogs (Cyera, Microsoft techcommunity, hivesecurity, Aptible) — not
  opened this session; leads staged in observation_queue instead of cited.
- Web search used for triage only; all evidence lines reference URLs opened directly.

## 2026-08-25
- opened: tool repos & releases via GitHub API — llama.cpp (v0.3.0 first v0.3.x tag +
  b10621/b10620, 2026-08-25; opened v0.3.0 release notes), Ollama (v0.32.15 stable /
  v0.33.0-rc3, 2026-08-21), vLLM (v0.27.1, 2026-08-11), LocalAI (v4.9.0, 2026-08-20),
  garak (v0.16.0, 2026-08-04), promptfoo (0.122.0, 2026-08-04), transformers (v5.15.1,
  2026-08-19). PyRIT: tags API returned empty — degraded (2nd run).
- opened: GHSA global advisory feed — sweep of latest 30; on-axis capture:
  GHSA-2cp2-2r3c-7p7r (Hydra, CVE-2026-68508, config-instantiation code execution).
  No new inference-server advisories since last scan.
- opened: papers — arXiv cs.CR recent listing; abstracts opened: 2608.23471 (InjecMEM),
  2608.21929 (SkillBloat), 2608.22868 (AgentFlow), 2608.22248 (AEGIS).
- opened: OWASP Top 10 for LLM Applications project page (legacy entry point; GenAI LLM
  Top 10 2026 published 2026-08-04, canonical repo GenAI-Security-Project/GenAI-LLM-Top10).
- degraded: r/LocalLLaMA JSON endpoint (reddit.com) — rejected again, 2nd consecutive run.
- Note: session sandbox started empty; repo state recovered by cloning the GitHub remote
  (public window granted by curator). See TRENDS.md#blockers.

## 2026-10-05 (first run after 41-day gap)
- opened: tool repos & releases via WebFetch (GitHub MCP scoped to radar repo only) —
  llama.cpp (b11405, 2026-10-05), Ollama (v0.35.1 stable 2026-09-29 / v0.40.0-rc3
  pre-release 2026-09-25), vLLM (v0.31.0, 2026-10-05), LocalAI (v4.11.0, 2026-10-02),
  garak (v0.17.0, 2026-09-09; opened release notes), promptfoo (0.123.1, 2026-09-18),
  transformers (v5.18.0, 2026-09-30). PyRIT: ARCHIVED 2026-03-27 — no releases page.
- opened: GHSA — GHSA-6hc7-9rph-cm99 (llama.cpp CVE-2026-43631, UAF CVSS 9.2);
  GHSA global feed sweep (limited to pip/high+critical); 3 on-axis advisories found
  (headroom-ai, vibe-trading-ai, jupyterlab XSS).
- opened: Cyera blog — "Breaking Local AI Runtimes" (10 llama.cpp vulnerabilities);
  "Bleeding Llama" (Ollama CVE-2026-7482 detail + ~300k exposed servers claim).
- opened: Sysdig blog — CVE-2026-33626 LMDeploy SSRF exploited in-the-wild in 12h31m.
- opened: StingRAI blog — inference server CVE roundup (Triton, vLLM, Ollama, llama.cpp).
- opened: Zafran Labs — FaceHugger: 3 CVEs in HF diffusers (TOCTOU bypass trust_remote_code).
- opened: HelpNetSecurity — Hugging Face breach by autonomous AI agent (Jul 20, 2026).
- opened: BleepingComputer — Hugging Face breach details (dataset-loader + template-injection).
- opened: papers — arXiv cs.CR recent listing (2026-10-05): 13 on-axis papers identified;
  abstracts opened: 2609.03884 (HookPry), 2610.03448 (PI detector re-eval), 2610.02302
  (intent-hiding jailbreaks), 2605.17634 (impossibility result), 2608.05659 (ARIA
  instruction backdoors), 2608.15913 (conjunctive poisoning).
- opened: Ollama v0.35.1 release notes (Clef decision models, capabilities).
- opened: garak v0.17.0 release notes (EU AI Act mapping, Ollama generator fixes).
- opened: vLLM releases page (v0.31.0 through v0.28.0 triage).
- web search used for triage: GHSA AI/ML CVEs, arXiv LLM security papers, MCP tool
  poisoning, HuggingFace supply chain, OWASP GenAI 2026, NVIDIA Triton CVEs, consumer
  GPU inference, fine-tuning frameworks. All evidence lines reference URLs opened directly.
- degraded: NVIDIA security bulletin (nvidia.custhelp.com) — HTTP 403; Triton CVE data
  verified via StingRAI roundup instead.
- degraded: Microsoft "State of MCP Security 2026" (techcommunity.microsoft.com) — page
  returned empty content; topic covered by independent sources.
- degraded: r/LocalLLaMA — not attempted this run (degraded 2+ prior runs; no new access
  method available). 3rd consecutive degraded.
- degraded: cybersecuritynews.com (OWASP article) — empty content; topic confirmed via
  other secondary search results.
- Note: 41-day gap since last scan. State persisted via GitHub remote this time (cloned
  to working branch). GitHub MCP was scoped to radar repo only — external repo queries
  required WebFetch fallback.

## 2026-10-21 (first daily since 2026-10-05; 16-day gap)
- opened: tool repos & releases via WebFetch — llama.cpp (b11774–b11785, 2026-10-21;
  b11780 adds WebSocket auth, b11776 speculative-decoding logprobs, b11781 TTS endpoint),
  Ollama (v0.40.7, 2026-10-18; pplx-decider 27B model), vLLM (v0.32.0, 2026-10-18; FP8
  KV cache default for GLM-5.x, security fixes CVE-2026-73560 SSRF patched, CORS default
  change), LocalAI (v4.11.0 still latest, 2026-10-02), garak (v0.17.1, 2026-10-16;
  hit@k metric, Python 3.14), promptfoo (0.124.1, 2026-10-08 still latest), transformers
  (v5.20.2, 2026-10-19; multimodal generate fix), Unsloth (v0.1.909-beta, 2026-10-19;
  multi-GPU FSDP2, Vulkan non-NVIDIA, adamw_flash), ExLlamaV3 (repo page opened, v0.0.6
  still latest release, added DeepSeek V4/Gemma 4/Qwen 3.5 MoE architectures), PyRIT
  (not checked — last at v1.1.0 Sep 4), MITRE ATLAS navigator data (v1.14.0 Feb 6,
  ATLAS Data 5.4.0).
- opened: GHSA — individual advisories: GHSA-fr42-jr2w-mx59 (Ollama CVE-2026-108836
  SSRF, Moderate), GHSA-4hhp-h66f-j5j7 (vLLM CVE-2026-73560 SSRF, Moderate, patched
  0.26.0), GHSA-865q-vfjv-p93j (Open WebUI CVE-2026-109572 privilege escalation, High),
  GHSA-7pf8-cp62-gc3p (ChatOllama CVE-2026-111702 IDOR, High), GHSA-h36v-27jx-93r3
  (Portkey AI Gateway CVE-2026-110719 SSRF, Moderate), GHSA-qf42-fp6f-25w9 (Langflow
  CVE-2026-107366 authz bypass, High), GHSA-chcq-pfxc-99ww (9router CVE-2026-108593
  config injection, High). GHSA listing page for AI front-end/gateway advisories opened
  (25 of 202 unreviewed results).
- opened: papers — arXiv cs.CR recent listing (2026-10-21): 18+ on-axis papers identified;
  abstracts opened: 2610.28425 (CarryoverBench — persistent memory carryover attacks),
  2610.27620 ("Local Allow, Global Deny" — authorization composability impossibility),
  2610.27244 (AutoRedClaw — automated agent red-teaming), 2610.28364 (nokast-secureRAG —
  PI detection in RAG), 2610.28397 (MAS-Guard — multi-agent guardrails), 2610.28484
  (Proof-Carrying Contracts), 2610.26935 (intervention history vs agent sabotage),
  2610.27383 (AgenticVulHunter — local agentic vuln hunting). arXiv cs.CL recent listing:
  2610.27908 (polarity blindness in LLM safety).
- opened: MITRE CTID blog — "Secure AI v2 Release" (2026-05-06); confirms ATLAS v5.4.0
  with 45+ agentic AI techniques, monthly release cadence, Knowledge Graph.
- degraded: protectai.com/blog — HTTP 404 (1st consecutive).
- degraded: hiddenlayer.com/blog/ — HTTP 404 (1st consecutive).
- degraded: r/LocalLLaMA — not attempted (degraded 4+ consecutive runs; no new access
  method available).
- web search used for triage: llama.cpp KV cache quantization, MITRE ATLAS 2026, local
  LLM red-team tools, Open WebUI CVE details. All evidence lines reference URLs opened
  directly.
- Note: 16-day gap since last scan (2026-10-05). First daily run since then. Vendor/lab
  blog feeds (protectai, hiddenlayer) returned 404; remaining 8 vendor blogs not attempted
  this run — flagged for next run.
