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

## 2026-10-15 (daily, first run since 10-05)
- opened: tool repos & releases via WebFetch (GitHub release pages) —
  llama.cpp (b11642, 2026-10-15), Ollama (v0.40.4 stable 2026-10-12 / v0.40.5-rc0
  pre-release 2026-10-14; v0.40.4 release notes opened), vLLM (v0.31.0, 2026-10-05),
  LocalAI (v4.11.0, 2026-10-02), garak (v0.17.0, 2026-09-09), promptfoo (0.124.1,
  2026-10-08), transformers (v5.19.0, 2026-10-06). PyRIT (v1.1.0, 2026-09-04; release
  notes opened — Best-of-N scanner, ShieldGemma, 488 jailbreak templates).
- opened: GHSA — global feed sweep (reviewed/pip/critical): 14 on-axis advisories
  identified Sep 8–Oct 8; individually opened: GHSA-g5f9-3xfg-p9mf (Decepticon
  CVE-2026-61732, ChatML injection CVSS 10.0), GHSA-6qxp-vccf-f47h (MCP SDK
  CVE-2026-104850, OAuth credential theft CVSS 7.5), GHSA-7m6h-x95x-82q5 (vLLM
  CVE-2026-73558, cross-user data leak CVSS 5.3), GHSA-2vh9-42vm-xmv2 (LMDeploy
  CVE-2025-66455, pickle RCE CVSS 9.8), GHSA-w794-rj3p-xv45 (Langflow CVE-2026-105697,
  MCP stdio RCE CVSS 9.9), GHSA-2xv2-w8cq-5gxw (PraisonAI CVE-2026-61447, unsandboxed
  code CVSS 10.0). GHSA high/pip sweep returned empty (filter issue).
- opened: papers — arXiv cs.CR recent listing (2026-10-14): 12 on-axis papers identified
  from 141 entries (first 50 shown); abstracts opened: 2610.18457 (Kairos transactional
  security), 2610.17457 (BrowseSafe++ PI detection benchmark), 2610.17313 (TRAP automated
  jailbreaking), 2610.19422 (AgentSafeEvo adversarial co-evolution), 2610.18430 (FedGraph
  federated LLM backdoor defense), 2610.17820 (safety judge comparison).
- opened: OWASP GenAI LLM Top 10 2026 download page (genai.owasp.org) — confirmed
  published Aug 3 2026, v1.0. Announcement page opened (Sep 2 2026). Full item list not
  retrieved (PDF download required).
- opened: MITRE ATLAS navigator data releases (github.com/mitre-atlas) — v1.14.0 (Feb
  2026, ATLAS Data 5.4.0); v2026.09 update reported by secondary sources only.
- opened: NVD CVE-2026-34159 — redirected to NVD home (no content); llama.cpp CVE details
  from secondary vuln databases only (CVE-2026-34159 RPC RCE CVSS 9.8, CVE-2026-43628 DRY
  sampler CVSS 8.5, CVE-2026-43632 tokenization race CVSS 8.1).
- web search used for triage: llama.cpp CVEs, AI ML security advisories Oct 2026, arXiv
  LLM security Oct 2026, MCP server security, malicious HuggingFace models, OWASP GenAI
  2026, MITRE ATLAS 2026, Ollama v0.40 CVEs, vLLM cross-user leak, consumer GPU inference,
  Unsloth fine-tuning, r/LocalLLaMA community. All evidence lines reference URLs opened
  directly.
- degraded: NVD (nvd.nist.gov) — CVE detail pages redirect to homepage; enrichment
  limited per April 2026 NIST restructuring.
- degraded: vendor blog primary feeds (Microsoft, Google, Anthropic, OpenAI, Protect AI,
  HiddenLayer, Lakera, Trail of Bits, Wiz, Elastic) — web search found no October 2026
  posts; individual blog indexes not opened this run. Coverage gap persists.
- degraded: r/LocalLLaMA — not attempted this run (degraded 3+ prior runs; reddit.com
  JSON endpoint blocked). 4th consecutive degraded.
- degraded: arXiv cs.CR listing showed only 50/141 Oct 14 entries; earlier October
  listings not retrieved.
