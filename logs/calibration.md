# Calibration log

Append-only. One dated line per weekly self-evaluation. Format:

    YYYY-Wnn — queue +A/-D (live L) · evidence E, stages +S · explore X/7 · off-axis P% · coverage s/t · capture-leak n/m · source-discovery s/p
2026-W40 — queue +0/-1 (live 7) · evidence 1, stages +0 (2 seed→dormant) · explore 0/7 · off-axis 0% (1/1 on existing trend) · coverage 0/30 (no daily runs; weekly opened only NVD + Ollama atom) · capture-leak 0/0 · source-discovery 0/0
2026-W41 — queue +0/-4 (live 5) · evidence 2, stages +0 · explore 0/7 · off-axis 0% (2/2 on existing trends) · coverage 11/25 (vendor blogs unlogged) · capture-leak 0/0 · source-discovery 0/0
2026-W42 — queue +3/-4 (live 7 incl. 4 resolved-markers excluded) · evidence 7, stages +0 · explore 0/7 · off-axis 0% (7/7 on existing trends) · coverage 0/25 daily (weekly opened GHSA, Ollama + Unsloth releases, arXiv cs.CR) · capture-leak 0/0 · source-discovery 0/0 (Unsloth added directly, verified)
2026-W43 — queue +4/-2 (live 5) · evidence 10, stages +2 (1 emerging→accelerating, 1 new seed) · explore 0/7 · off-axis 50% (5/10 on existing trends, 5/10 on new llm-frontend-001) · coverage 7/27 weekly-opened (0/27 via daily runs) · capture-leak 0/0 · source-discovery 0/0 (Wiz, Trail of Bits, Anthropic verified; GHSA app-layer queries added)
2026-W44 — queue +8/-1 (live 8) · evidence 5, stages +2 (1 seed→emerging ai-supplychain-001, 1 emerging→accelerating local-inference-001 ratified) · explore 2/7 · off-axis 100% (5/5 on existing trends) · coverage 18/28 (3 degraded, 6 never opened) · capture-leak 0/0 · source-discovery 1/1 (Sysdig verified and added)
2026-11 retrospective — Missed: the 1b engineering stack (quantization, KV-cache, ExLlamaV3/Unsloth) has releases in the tools block but zero ledger trend; taxonomy axis (ATLAS/OWASP) unopened for 3 weeks. Over-tracked: arXiv agent-skill papers (agentic-injection-001 is saturated at 10/10 evidence, so new items only reach notes). Local-model axis: depth is good on security (inference servers) but thin on build-stack signal and community pulse (r/LocalLLaMA degraded 6+ runs).
2026-W45 — queue +1/-1 (live 6) · evidence 2, stages +0 (local-inference-001 accelerating held) · explore 1/7 · off-axis 100% (2/2 on existing trend) · coverage 5/28 weekly-run opens (NVD, huntr, Lakera, Elastic healed; daily 11-06 covered ~18) · capture-leak 0/0 · source-discovery 0/0
