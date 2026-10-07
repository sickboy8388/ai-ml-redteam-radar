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

## 2026-10-07
- opened: tool repos & releases via WebFetch (GitHub release pages) —
  llama.cpp (b11461, 2026-10-07), Ollama (v0.40.0 2026-09-25 / v0.35.1 2026-09-29),
  vLLM (v0.31.0, 2026-10-05), LocalAI (v4.11.0, 2026-10-02),
  garak (v0.17.0, 2026-09-09), promptfoo (0.124.0, 2026-10-06),
  transformers (v5.18.0, 2026-09-30).
  PyRIT: CORRECTED — github.com/microsoft/PyRIT is active (v1.1.0, Sep 4);
  Azure/PyRIT is an archived stub.
  ExLlamaV3: verified at turboderp-org/exllamav3 (v1.5.4, 2026-10-03; repo + releases
  page opened).
- opened: GHSA — GHSA-q8gq-377p-jq3r (vLLM CVE-2026-41523, assert bypass → RCE via
  malicious HuggingFace model, CVSS 7.5, fixed 0.22.0). GHSA global feed search
  (pip/high+critical): no additional on-axis advisories found.
- opened: CVE-2026-34159 via SentinelOne vuln DB (secondary; llama.cpp RPC memory R/W
  CVSS 9.8, fixed b8492) — NVD/GHSA primary not opened; queued for next run.
- opened: papers — arXiv cs.CR recent listing (2026-10-07); abstracts opened:
  2610.07645 (SkillPoison: progressive skill poisoning, 95.71% ASR),
  2610.07639 (HarnessSecurity-Bench: coding-agent harness security, 95.6% ASR with
  auto-approval), 2610.07125 (PEV: embedding perturbation jailbreak, 100% on
  JailbreakBench), 2610.08571 (RAG-PIBench: PI detection benchmark for RAG),
  2610.07723 (answer-side backdoor: model-planted triggers, ~100% ASR at 5% poisoning).
- opened: OWASP GenAI LLM Top 10 2026 — genai.owasp.org/resource/owasp-genai-llm-top-10-2026/
  (confirmed published 2026-08-03; incident-weighted methodology). Canonical OWASP
  project page also opened (owasp.org).
- opened: Unsloth MoE fine-tuning — unsloth.ai/docs/basics/faster-moe and
  unslothai.substack.com blog (2026-02-10); 12x MoE speedup, gpt-oss-20b on 12.8GB VRAM.
- web search used for triage: GHSA AI/ML CVEs, arXiv LLM security papers Oct 2026,
  vLLM CVE-2026-41523, OWASP GenAI 2026, ExLlamaV3, Unsloth MoE, PyRIT status,
  llama.cpp CVEs Oct 2026, MCP server security, Promptfoo acquisition, Ollama MLX,
  r/LocalLLaMA community pulse, AI security tools 2026, vendor blogs. All evidence
  lines reference URLs opened directly.
- degraded: r/LocalLLaMA — not attempted (degraded 3+ prior runs, no new access method).
  4th consecutive degraded.
- degraded: vendor blogs (protectai.com, hiddenlayer.com, lakera.ai) — search returned
  no October 2026 blog posts; no new on-axis content identified.
