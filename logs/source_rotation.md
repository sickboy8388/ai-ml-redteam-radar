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

## 2026-10-25 (weekly W43 sweep; no daily ran)
- opened: GHSA search listings (ollama, open-webui) + advisories GHSA-h36v-27jx-93r3, GHSA-j8f7-x8jm-wmm4, GHSA-fr42-jr2w-mx59, GHSA-7pf8-cp62-gc3p, GHSA-865q-vfjv-p93j.
- opened: arXiv cs.CR recent (2026-10-23) + abstracts 2610.30418, 2610.31404, 2610.30365.
- opened: github.com/ollama/ollama/releases (v0.40.7–0.40.11); github.com/ggml-org/llama.cpp/releases (b11871).
- opened: Trail of Bits blog, Wiz blog (+ LiteLLM post), Anthropic research index.
- web search (triage only): LiteLLM compromise Oct 2026 — results not opened except Wiz.
- not opened this week: Microsoft, DeepMind, OpenAI, Protect AI, HiddenLayer, Lakera, Elastic, vLLM, LocalAI, garak, promptfoo, PyRIT, ExLlamaV3, transformers, ATLAS, NVD, huntr, arXiv cs.CL, r/LocalLLaMA (coverage gap, scheduler outage).

## 2026-10-25 (daily, after W43 weekly)
- opened: tool repos & releases via WebFetch — vLLM (v0.32.0, 2026-10-18; v0.31.0 recap; 3 security fixes), LocalAI (v4.12.1 2026-10-23 security-only patch, v4.12.0 2026-10-22), garak (v0.17.1 2026-10-16), promptfoo (0.125.0 2026-10-23), ExLlamaV3 (v1.6.4 2026-10-20; 10 releases v1.5.0–v1.6.4 with ROCm + Turing + consumer GPU focus), Unsloth (v0.1.910 2026-10-23; Vulkan backend, Flint 40B MoE), transformers (v5.20.2 2026-10-19), PyRIT (v1.1.0 2026-09-04).
- opened: GHSA reviewed advisory listing (pip, High+Critical) — captured vLLM batch (≥12 GHSAs Oct 5–23), Langflow batch (8 GHSAs Oct 5–7 incl. 3 Critical), LMCache CVE-2026-105192 (Critical).
- opened: individual advisories GHSA-w794-rj3p-xv45 (Langflow MCP cmd injection), GHSA-cf6m-vc3m-7cgm (Langflow webhook bypass), GHSA-w5f2-9q9c-ff4h (LMCache RCE), GHSA-gx7p-2j49-hfq4 (vLLM DoS).
- opened: Anthropic research index + posts (alignment assessment of cybersecurity incidents 2026-09-09, investigating unintended model actions 2026-10-09).
- opened: Wiz blog index + posts (From Phishing to LLMjacking 2026-10-20, Anatomy of AI-Driven Cloud Attacks 2026-10-19, PHP2Shell 2026-10-21).
- opened: Microsoft Security Blog AI red team topic page + LiteLLM supply-chain compromise analysis (2026-10-23) + FORGE Lab 3 lessons (2026-10-07).
- opened: arXiv cs.CL recent listing (2026-10-23) — no on-axis papers in first 50 of 117.
- web search (triage only): Anthropic UK AISI cybertesting (primary URL not found), Wiz blog URLs (found correct slugs), Microsoft ARTEX/Storm-0940 (secondary coverage only, primary URL not opened).
- degraded: Protect AI blog (protectai.com/blog) — HTTP 404. HiddenLayer blog (hiddenlayer.com/blog/) — HTTP 404. r/LocalLLaMA — not attempted (degraded 4+ prior runs).
- not opened this run: DeepMind, OpenAI, Lakera, Elastic, ATLAS, NVD, huntr, arXiv cs.CR new listing page (weekly already opened 10-23 listing).
