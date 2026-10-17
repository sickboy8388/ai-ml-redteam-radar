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

## 2026-10-17 (first daily since 2026-10-05; 12-day gap)
- opened: tool repos & releases via WebFetch —
  llama.cpp (b11706, 2026-10-17; memory error fixes in b11693, Beam model in b11701),
  Ollama (v0.40.5 Latest 2026-10-14 / v0.40.6 pre-release 2026-10-16; decision models, q2_0 tensor),
  vLLM (v0.31.0, 2026-10-05; no new release),
  LocalAI (v4.11.0, 2026-10-02; no new release),
  garak (v0.17.1, 2026-10-16; hit@k metric, Python 3.14),
  promptfoo (0.124.1, 2026-10-08; cost recording, OpenAI Decisions support),
  transformers (v5.20.1, 2026-10-16; Beam model, Muse Spark Open, Ling 3.0),
  ExLlamaV3 (v1.6.2, 2026-10-14; ROCm support v1.6.0, hybrid drafting v1.6.1, faster CPU offload),
  PyRIT (v1.1.0, 2026-09-04; no new release).
- opened: GHSA — GHSA-fr42-jr2w-mx59 (Ollama CVE-2026-108836, SSRF Pull API, Moderate CVSS 5.5, Oct 12).
  GHSA global feed sweep via search (no new high/critical pip advisories matched filter).
- opened: vLLM security/advisories tab — 5 new advisories Oct 6 (GHSA-h3rc-6mm3-gc2m RCE High,
  GHSA-823j-m4cj-hmjf memory exhaustion High, + 3 Moderate/Low); 3 advisories Sep 23;
  individual GHSA pages returned 404 (repository-level advisories).
- opened: papers — arXiv cs.CR October 2026 listing; abstracts opened:
  2610.01564 (APEX skill chaining), 2610.01508 (OverAct tool over-authorization),
  2610.01768 (LLMLeak covert exfil), 2610.01058 (MOMAT quantized LLM defense),
  2610.00450 (ZoneClaw memory-zoning), 2610.01349 (PACE capability enforcement),
  2610.00850 (AuraForge coding agent security), 2610.01535 (False Floors safety routing).
  arXiv cs.CL October listing: 2610.00320 (safety under fine-tuning) identified but not opened.
- opened: Unsloth Substack primary (2026-02-10): 12x MoE speedup, QLoRA, 500+ models confirmed.
  Observation_queue item resolved → study_shelf.
- opened: MITRE CTID blog (2026-05-06): Secure AI Phase 1 closed, 45+ techniques, agentic coverage.
- opened via search: MCP TypeScript SDK CVE-2026-104850 (Oct 6, High) identified via search;
  GHSA primary not opened (queued).
- degraded: vendor/lab blog feeds (Microsoft Security, Google DeepMind, Anthropic, OpenAI,
  Protect AI/huntr, HiddenLayer, Lakera, Trail of Bits, Wiz, Elastic) — search-only fallback
  used for triage; no individual blog pages opened this session.
- degraded: r/LocalLLaMA — not attempted (degraded 3+ prior runs, 4th+ consecutive).
- degraded: vLLM individual GHSA pages (GHSA-823j-m4cj-hmjf, GHSA-h3rc-6mm3-gc2m) — 404;
  verified via security/advisories listing instead.
- discovery: searched GitHub for awesome-llm-security lists (corca-ai last push Aug 2025,
  TalEliyahu Apr 2026) — no significant updates found.
- discovery: searched consumer GPU inference / ExLlamaV3 / GGUF quantization — EXL3 vs GGUF
  comparison coverage found; ExLlamaV3 rapid development confirmed via releases page.
- community pulse: searched HN — Kaspersky LLMjacking article (industrial-scale hijacking
  of self-hosted AI compute) noted; no October 2026 HN front-page thread found.
- exploration: MITRE ATLAS expansion and MCP ecosystem security scanned as off-axis exploration.
