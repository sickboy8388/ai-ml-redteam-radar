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

## 2026-10-24 (daily — first since 2026-10-05; 19-day gap)
- opened: tool repos & releases via WebFetch — llama.cpp (b11851, 2026-10-24), Ollama
  (v0.40.10 stable 2026-10-23 / v0.40.11-rc0 pre-release 2026-10-24), vLLM (v0.32.0,
  2026-10-18; release notes read with security fixes), LocalAI (v4.12.1 security patch
  2026-10-23 / v4.12.0 2026-10-22), garak (v0.17.1, 2026-10-16), promptfoo (0.125.0,
  2026-10-23), transformers (v5.20.2, 2026-10-19), Unsloth (v0.1.910-beta, 2026-10-23).
  PyRIT: no new release since v1.1.0 (Sep 4).
- opened: GHSA — search listing for ollama/vllm/open-webui/langflow/localai (25 results,
  all Oct 2026); individual advisories opened: GHSA-f623-hjm8-5wg5 (vLLM code injection),
  GHSA-vhg8-m8fr-3863 (LocalAI SSRF), GHSA-w5f2-9q9c-ff4h (LMCache pickle RCE),
  GHSA-4hhp-h66f-j5j7 (vLLM SSRF MiMoV2Omni), GHSA-865q-vfjv-p93j (Open WebUI priv esc),
  GHSA-crcq-c44m-c92x (Open WebUI session cookie hijack), GHSA-7pf8-cp62-gc3p (ChatOllama
  IDOR), GHSA-qf42-fp6f-25w9 (Langflow ownership bypass), GHSA-gx7p-2j49-hfq4 (vLLM
  mm_processor_kwargs DoS), GHSA-fr42-jr2w-mx59 (Ollama Pull API SSRF).
- opened: papers — arXiv cs.CR recent listing (2026-10-23, 50/51 entries): on-axis papers
  identified; abstracts opened: 2610.30418 (Agent Mosaic), 2610.31404 (AgentPhishing),
  2610.30202 (MPIDetector), 2610.30738 (AgentTriage). arXiv cs.CL recent listing checked
  (1 marginally on-axis paper, 2610.31047 harm/moderation).
- opened: vLLM v0.32.0 release notes — 3 reviewed security fixes + CORS + image + schema
  hardening. v0.31.0 reviewed (per-request mm_processor_kwargs + LoRA cache salt).
- opened: Ollama v0.40.2–v0.40.11-rc0 release notes (Oct 8–24) — Nemotron 3.5, Recursive
  Flint 40B MoE, Phonon speech, d3 decision models, background model upgrades.
- opened: LocalAI v4.12.1 release notes — URL redirect hardening security patch.
- opened: Unsloth v0.1.906–v0.1.910 release notes — REAP expert pruning, emSign cert
  rejection, API key sandboxing, MoE GGUF speedup.
- web search used for triage: Wiz blog AI security Oct 2026, LLM jailbreak/prompt injection
  tools Oct 2026, MITRE ATLAS 2026 updates. ATLAS v5.4.0 found via secondary source
  (agentmarketcap.ai) — queued for primary verification.
- degraded: Protect AI blog (protectai.com/blog) — HTTP 404. HiddenLayer blog
  (hiddenlayer.com/blog/) — HTTP 404. Both may have restructured URLs.
- degraded: r/LocalLLaMA — not attempted (4th+ consecutive degraded run; no new method).
- degraded: GHSA-q97c-p368-75c4, GHSA-frvg-qw88-hww9 — HTTP 404 on individual advisory
  pages (possibly withdrawn or GHSA IDs from vLLM release notes were provisional).
- Note: web access functional for GitHub, arXiv, and web search. Vendor blog lane still
  uncovered (Protect AI, HiddenLayer, Wiz, Microsoft, etc. — all 404 or no Oct results).
