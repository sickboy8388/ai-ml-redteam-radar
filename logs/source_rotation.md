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

## 2026-10-14
- opened: tool repos & releases via WebFetch — llama.cpp (b11609, 2026-10-14; b11608 DoS
  fix verified), Ollama (v0.40.4, 2026-10-12; release notes verified), vLLM (v0.31.0,
  2026-10-05; 10 security fixes verified on release page), LocalAI (v4.11.0, 2026-10-02),
  garak (v0.17.0, no change), promptfoo (0.124.1, 2026-10-08), transformers (v5.19.0,
  2026-10-06), PyRIT (v1.1.0, no change), ExLlamaV3 (v1.6.1, 2026-10-10; release notes
  verified — ROCm, Turing, reduced VRAM), Unsloth (v0.1.907, 2026-10-13; GitHub releases
  page verified).
- opened: GHSA — 25 advisories swept and verified on GHSA pages. On-axis captures:
  GHSA-w8p2-phwr-px3r (Ollama CVE-2026-103663, path traversal RCE CVSS 9.4),
  GHSA-3g9g-qh2j-c5q8 (llama.cpp CVE-2026-107183, UAF CVSS 9.2),
  GHSA-8wc5-pcgr-pg48 (vLLM CVE-2026-109311, audio heap overflow),
  GHSA-fr42-jr2w-mx59 (Ollama CVE-2026-108836, SSRF),
  GHSA-w7x8-q2gp-5cgg (Flowise CVE-2026-73487, prompt injection RCE CVSS 9.0),
  GHSA-8qpj-27x8-pwpq (Langflow CVE-2026-10561, unsandboxed Python CVSS 9.9),
  plus PraisonAI 7-advisory cluster, LangChain MongoDB/Redis, Open WebUI, HF TEI,
  TinyLLaVA, Banks, OpenLIT, Katanemo Plano.
- opened: papers — arXiv cs.CR + cs.CL recent listings; 25 on-axis papers verified:
  2610.18457 (Kairos), 2610.08951 (ASPIRE), 2610.09264 (PackHallu), 2610.18262 (encrypted
  skill injection), 2610.13623 (APEX-Harm), 2610.15153 (life-support agent hijack),
  2610.18508 (SA-CUA), 2610.12524 (cross-agent propagation), 2610.15177 (CoDA),
  2610.18326 (Jev-Guard), 2610.17313 (TRAP jailbreak), 2610.16305 (ATTCK-R),
  2610.16470 (CircuitBreak), 2610.15207 (depth-based inference jailbreak),
  2610.13078 (attention-MLP safety), 2610.10276 (PatchBench), 2610.17457 (BrowseSafe++),
  2610.16814 (StableJudge), 2610.17820 (judge comparison), 2610.18612 (Nudge the Judge),
  2610.17837 (ProtoArena), 2610.18430 (FedGraph), 2610.18609 (DPOison-VL),
  2610.18359 (watermark displacement), 2610.18408 (PI probe cues).
  Also verified: 2602.22242 (jailbreak defense bypass via reasoning prompts).
- opened: vendor blogs (FIRST TIME logged) —
  Microsoft Security Blog: 3 posts (FORGE Lab/MDASH Oct 7, CISO perspectives Oct 6,
  Digital Defense Report Oct 1); Wiz blog: 2 posts (AI SAST Oct 6, Red Agent Oct 7);
  Lakera blog: opened, no Oct 2026 posts; Trail of Bits blog: opened, no AI posts in window.
- opened: Unsloth Substack primary (Feb 10 2026 MoE update — verified 12x speed, VRAM claims).
- opened: MITRE CTID blog (Secure AI v2, May 6 2026 — 45+ new techniques, threat emulation).
- opened: MITRE ATLAS navigator-data releases (v1.14.0, Feb 6 2026, ATLAS Data 5.4.0).
- opened: CSA Agentjacking research note (Jun 14 2026 — Sentry MCP injection, 85% success).
- opened: InfoWorld/HiddenLayer malicious HF model report (May 11 2026 — 244k downloads).
- degraded: protectai.com/blog — HTTP 404; blog URL may have changed.
- degraded: hiddenlayer.com/blog/ — HTTP 404; blog URL may have changed.
- degraded: r/LocalLLaMA — not attempted (degraded 3+ prior runs; no new access method).
- Note: first daily run since 2026-10-05. Full sweep executed. Vendor blog gap partially
  resolved (4 of 6 opened). Web search used for triage only; all evidence lines reference
  URLs opened directly.
