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

## 2026-10-22 (daily — first since 2026-10-05)
- opened: tool repos & releases via WebFetch —
  llama.cpp (b11809, 2026-10-22; b11798–b11809 triaged),
  Ollama (v0.40.8 stable 2026-10-21, v0.40.9-rc1 2026-10-22),
  vLLM (v0.32.0, 2026-10-18; full release notes opened incl. security advisories),
  LocalAI (no new release since v4.11.0),
  garak (v0.17.1, 2026-10-16; release notes opened),
  promptfoo (0.124.1, 2026-10-08; 0.124.0, 2026-10-06; release notes opened),
  transformers (v5.20.2 2026-10-19, v5.20.0 2026-10-15; release notes opened),
  PyRIT (no new release since v1.1.0),
  ExLlamaV3 (v1.6.4 2026-10-20; v1.6.0–1.6.4 triaged; ROCm, tensor-parallel, hybrid drafting),
  Unsloth (v0.1.909, 2026-10-19; release notes opened).
- opened: GHSA —
  GHSA-w5f2-9q9c-ff4h (LMCache CVE-2026-105192, Critical 9.8, pickle RCE),
  GHSA-fr42-jr2w-mx59 (Ollama CVE-2026-108836, Moderate, SSRF in Pull API),
  GHSA-4hhp-h66f-j5j7 (vLLM CVE-2026-73560, Moderate, MiMoV2 SSRF),
  GHSA-f2ph-cmg5-wxc8 (Storybook MCP addon CVE-2026-114125, Critical 9.4).
  GHSA global search (published >2026-10-15 + ML/LLM/inference terms): LMCache and Storybook
  MCP hits; remaining results non-AI.
- opened: vLLM v0.32.0 release page — 3 security GHSAs (chat template DoS, tokenizer
  off-by-one, P2P socket exhaustion) + CORS deny-by-default + image-format restrictions +
  HMAC-signed multimodal cache handles.
- opened: papers — arXiv cs.CR October listing; abstracts opened:
  2610.01349 (PACE tool-call enforcement), 2610.01508 (OverAct over-authorization),
  2610.01564 (Chaining Skills / APEX skill-chain hijacking),
  2610.01768 (LLMLeak covert exfiltration via web-fetch),
  2610.01367 (data poisoning after quality selection).
  arXiv cs.CL October listing: 2610.00320 (refusal localization), 2610.00568 (emergent
  unfaithfulness). Listing only — full months would need deeper traversal.
- opened: vendor blogs —
  Trail of Bits blog (blog.trailofbits.com): 3 Oct posts identified; "Package managers have
  an integrity problem" (Oct 14, supply-chain relevant) and "AI agent patch delegation"
  (Oct 21, agentic relevant).
- degraded: Protect AI blog (protectai.com/blog) — HTTP 404.
- degraded: HiddenLayer blog (hiddenlayer.com/blog/) — HTTP 404.
- degraded: Lakera blog (lakera.ai/blog) — no October 2026 posts found on page.
- degraded: r/LocalLLaMA — not attempted (degraded since 2026-08-24; 4+ runs).
- web search used for triage: GHSA AI/ML CVEs Oct 2026, LMCache CVE-2026-105192, Open WebUI
  CVE-2026 (secondary aggregator results — primaries not opened), LLM red team tools 2026,
  llama.cpp GGUF/KV-cache/speculative Oct 2026, MITRE ATLAS 2026, Protect AI/huntr Oct 2026,
  Hacker News LLM security Oct 2026. All evidence lines reference URLs opened directly.
- Note: 17-day gap since last daily (2026-10-05); weekly ran 2026-10-18. Web access
  functional. 3 vendor blog feeds (Protect AI, HiddenLayer, Lakera) returned 404/empty —
  URLs may have changed; investigate on next run.
