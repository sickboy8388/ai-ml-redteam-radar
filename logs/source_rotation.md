# Source rotation log

Append-only. One dated entry per run: which sources were `opened` or `degraded: <reason>`.

## 2026-08-24 (first run) LocalAI
  (v4.9.0, 2026-08-20), garak (v0.16.0, 2026-08-04, opened full release notes), promptfoo
  (0.122.0, 2026-08-04), transformers (v5.15.1, 2026-08-19). PyRIT: no releases feed
  (tags-based distribution — track via tags in future runs).
- opened: tool repos & releases via GitHub API — llama.cpp (b10604, 2026-08-24), Ollama
  (v0.32.15 stable / v0.33.0-rc2, 2026-08-21), vLLM (v0.27.1, 2026-08-11),
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
  b10621/b10620, 2026-08-25; opened v0.3.0 release notes), Ollama (v0.32
Resolving conflicts between claude/zen-lamport-nl45gx and main and committing changes  claude/zen-lamport-nl45gx
3 conflicting files
README.md
README.md
TRENDS.md
TRENDS.md
source_rotation.md
logs/source_rotation.md
logs/source_rotation.md
.15 stable /
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
- opened: arXiv cs.CR recent (2026-10-23) + abstracts 2610.30418, 2610.31404,W43 sweep; no daily ran
## 2026-10-25 (weekly )
- opened: GHSA search listings (ollama, open-webui) +- opened: github.com/ollama/ollama/releases (v0.40.7–0.40.11); github.com/ggml-org/llama.cpp/releases (b11871).
 advisories GHSA-h36v-27jx-93r3, GHSA-j8f7-x8jm-wmm4, GHSA-fr42-jr2w-mx59, GHSA-7pf8-cp62-gc3p, GHSA-865q-vfjv-p93j.
 2610.30365.
- opened: Trail of Bits blog, Wiz blog (+ LiteLLM post), Anthropic research index.
- web search (triage only): LiteLLM compromise Oct 2026 — results not opened except Wiz.
- not opened this week: Microsoft, DeepMind, OpenAI, Protect AI, HiddenLayer, Lakera, Elastic, vLLM, LocalAI, garak, promptfoo, PyRIT, ExLlamaV3, transformers, ATLAS, NVD, huntr, arXiv cs.CL, r/LocalLLaMA (coverage gap, scheduler outage).

## 2026-10-26 (daily)
- opened: tool repos & releases — llama.cpp/releases (b11879-b11889, Oct 25-26), Ollama/releases (v0.40.11 still latest), vLLM/releases (v0.32.0, Oct 18: 3 security fixes, NVFP4 KV cache on Ada), LocalAI/releases (v4.12.0 Oct 22, v4.12.1 Oct 23 security-only SSRF hardening), garak/releases (v0.17.1, Oct 16), promptfoo/releases (0.124.0-0.125.1, Oct 6-25), ExLlamaV3/releases (1.6.2-1.6.5, Oct 14-25), Unsloth/releases (v0.1.909-0.1.910, Oct 19-23), transformers/releases (v5.19.0-v5.20.2, Oct 6-19).
- opened: GHSA search listings (pip high/critical; vllm; ollama) — vLLM: 19+ new GHSAs Oct 21-25 (Critical CVE-2026-114053, multiple High). Individual advisories opened: GHSA-f623-hjm8-5wg5 (vLLM Critical code injection), GHSA-6vc9-vh4h-cxh4 (vLLM High resource exhaustion), GHSA-4hhp-h66f-j5j7 (vLLM Moderate SSRF). No new Ollama advisories beyond W43 weekly.
- opened: arXiv cs.CR recent (Mon 26 Oct listing, 38 entries) — 6 on-axis papers: 2610.32531 (NTBench near-target PI), 2610.32155 (KnotScryer insecure skill compositions), 2610.31974 (MCP provenance binding), 2610.31914 (agent tool auth minima), 2610.31695 (safety guard target rebinding), 2610.31366 (AfterDeleteBench post-deletion persistence). Also opened: 2610.32334 (code model backdoors via TNCS).
- opened: arXiv abstracts — 2610.30798 (LLVMhammer Rowhammer on LLM inference), 2610.30202 (MPIDetector multimodal PI detection).
- opened: Anthropic research index + posts — "Investigating unintended model actions" (Oct 9), "UK AISI cybertesting alignment assessment" (Oct 23).
- opened: Wiz blog index + "From Phishing to LLMjacking" (Oct 20); "Gheist" and "Anatomy of a Real AI-Driven Cloud Attack" returned 404.
- opened: Trail of Bits blog — no new AI-security posts since W43 weekly.
- web search (triage): GHSA for ollama/vllm/open-webui/litellm/langflow CVE 2026; arXiv cs.CR LLM security Oct 2026; Wiz LLMjacking; HN LLM security Oct 2026; LLM red team / MCP security new tools 2026.
- not opened this run: Microsoft, DeepMind, OpenAI, Protect AI, HiddenLayer, Lakera, Elastic, PyRIT, ATLAS, NVD, huntr, arXiv cs.CL, r/LocalLLaMA, awesome-lists (coverage gap, single-agent time budget).
- degraded: Wiz blog — 2 of 4 target URLs returned 404 (Gheist, Anatomy); the other 2 opened (LiteLLM, LLMjacking).
- degraded: GHSA pip high/critical listing — page returned "No results matched" (rendering issue); used per-project query instead.
- degraded: r/LocalLLaMA — not attempted (degraded 4+ consecutive runs, no new access method).
