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

## 2026-10-08
- opened: tool repos & releases via WebFetch — llama.cpp (b11491, 2026-10-08),
  Ollama (v0.40.1, 2026-10-07; opened release notes), vLLM (v0.31.0 still latest,
  2026-10-05), LocalAI (v4.11.0 still latest), garak (v0.17.0 still latest),
  promptfoo (0.124.0, 2026-10-06), transformers (v5.19.0, 2026-10-06).
- opened: ExLlamaV3 releases (github.com/turboderp-org/exllamav3) — v1.6.0 (Oct 7):
  ROCm support, faster CPU offloading. Verified queue item.
- opened: PyRIT releases (github.com/microsoft/PyRIT) — v1.1.0 (Sep 4), v1.0.0 GA
  (Jul 24). Project active, Azure/PyRIT was archived stub. Updated SOURCES.md.
- opened: GHSA-q8gq-377p-jq3r — vLLM CVE-2026-41523 code injection via assert bypass;
  CVSS 7.5, fixed 0.22.0. Published Jun 14.
- opened: GHSA-8wr5-jm2h-8r4f — vLLM CVE-2026-54234 remote DoS via speculative decoding;
  CVSS 7.5, fixed 0.24.0. Published Jul 2.
- opened: OWASP GenAI LLM Top 10 2026 canonical page (genai.owasp.org) — confirmed
  published Aug 3 2026 v1.0. Agent Control Standard Sep 1.
- opened: Unsloth 2026 Update blog (unslothai.substack.com) — Feb 10 2026: MoE 12x
  faster, 35% less VRAM. Verified queue item.
- opened: papers — arXiv cs.CR recent listing (2026-10-08, 50 entries): 17+ on-axis
  papers identified. Abstracts opened: 2610.09469 (Secure-CUA), 2610.09264 (PackHallu),
  2610.09240 (WebMirage), 2610.08951 (ASPIRE), 2610.08871 (CredLeakBench),
  2610.09793 (formal runtime verification), 2610.09027 (visual KV-cache attacks).
- opened: arXiv cs.CL recent listing (2026-10-08, partial): 2610.09772 (decoupled
  edge LLM agents).
- web search used for triage: GHSA AI/ML CVEs Oct 2026, MCP server security 2026,
  PyRIT status, ExLlamaV3, Unsloth, OWASP GenAI 2026, llama.cpp speculative decoding,
  Hacker News AI security. All evidence lines reference URLs opened directly.
- degraded: r/LocalLLaMA — not attempted this run (degraded 3+ prior runs). 4th
  consecutive degraded.
- degraded: NVIDIA security bulletin (nvidia.custhelp.com) — not retried; prior 403
  still expected.
- Note: 3-day cadence restored (Oct 5 → Oct 8). GitHub MCP still scoped to radar repo
  only — WebFetch used for external repos.
