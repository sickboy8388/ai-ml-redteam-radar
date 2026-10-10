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

## 2026-10-10
- opened: tool repos & releases via WebFetch —
  llama.cpp (b11540, 2026-10-10), Ollama (v0.40.2, 2026-10-08 / v0.40.1, 2026-10-07),
  vLLM (v0.31.0, 2026-10-05 — no new release), LocalAI (v4.11.0, 2026-10-02 — no new
  release), garak (v0.17.0, 2026-09-09 — no new release), promptfoo (0.124.1, 2026-10-08),
  transformers (v5.19.0, 2026-10-06), ExLlamaV3 (v1.6.0, 2026-10-07).
- opened: ExLlamaV3 repo (turboderp-org/exllamav3) — active, EXL3 format, ROCm support,
  v1.6.0 release notes verified. ExLlamaV2 → ExLlamaV3 succession confirmed.
- opened: microsoft/PyRIT repo — active (2231 commits, 48 open PRs). Azure/PyRIT archived
  2026-03-27; development continued here.
- opened: GHSA advisory feed for SGLang — 29 advisories (7 critical) in 2026. Specific
  advisories opened: GHSA-w4hv-c72g-pqx6 (CVE-2026-93034, pickle deserialization in IPC,
  CVSS 9.8, Oct 8), GHSA-2wm4-697g-pfq8 (CVE-2026-5760, Jinja2 SSTI in chat template,
  CVSS 9.8, Apr 20).
- opened: CSA research note on SGLang CVE-2026-5760 — confirmed SSTI in getjinjaenv(),
  /v1/rerank endpoint, no sandboxed Jinja2, discoverer Stuart Beck / CERT/CC VU#915947.
- opened: Ollama v0.40.2 release notes — background model upgrades, no security fixes.
- opened: papers — arXiv cs.CR recent listing (Oct 9, 2026): 13+ on-axis papers identified.
  Abstracts opened: 2610.12463 (agent security incidents), 2610.11030 (NOMOS tool-call
  gates), 2610.10612 (PyCache Trap skill scanner bypass), 2610.11634 (LTBD prompt injection
  delimiters), 2610.10742 (BRANCH guardrail bypass), 2610.10735 (DITTO pickle scanner),
  2610.10929 (Speedbumps speculative decoding DoS), 2610.11843 (LLM weight exfiltration
  detection), 2610.11467 (GROB agentic activity investigation).
- opened: arXiv cs.CL recent listing (Oct 9) — 4 potentially on-axis (alignment
  generalization, intent recovery, constitutional gating, adversarial cues in judges).
- opened: OWASP GenAI LLM Top 10 2026 resource page (genai.owasp.org) — confirmed v1.0,
  2026-08-03; download-only PDF, could not extract categories.
- web search used for triage: GHSA AI/ML, SGLang CVEs, PyRIT replacement, Unsloth MoE,
  ExLlamaV3, OWASP GenAI 2026, MCP tool poisoning CVEs, AI security tools, r/LocalLLaMA.
  All evidence lines reference URLs opened directly.
- degraded: GHSA filtered search (pip/high+critical) — returned 0 results (rendering issue);
  fell back to specific advisory queries.
- degraded: r/LocalLLaMA (reddit.com) — 4th consecutive run without access; community-pulse
  lane uncovered. Secondary sources used for pulse context only.
- Note: state persisted via GitHub remote clone to feature branch. 5-day gap since last
  scan (2026-10-05 → 2026-10-10).
