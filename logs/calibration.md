# Calibration log

Append-only. One dated line per weekly self-evaluation. Format:

    YYYY-Wnn — queue +A/-D (live L) · evidence E, stages +S · explore X/7 · off-axis P% · coverage s/t · capture-leak n/m · source-discovery s/p
2026-W40 — queue +0/-1 (live 7) · evidence 1, stages +0 (2 seed→dormant) · explore 0/7 · off-axis 0% (1/1 on existing trend) · coverage 0/30 (no daily runs; weekly opened only NVD + Ollama atom) · capture-leak 0/0 · source-discovery 0/0
2026-W41 — queue +0/-4 (live 5) · evidence 2, stages +0 · explore 0/7 · off-axis 0% (2/2 on existing trends) · coverage 11/25 (vendor blogs unlogged) · capture-leak 0/0 · source-discovery 0/0
2026-W42 — queue +3/-4 (live 7 incl. 4 resolved-markers excluded) · evidence 7, stages +0 · explore 0/7 · off-axis 0% (7/7 on existing trends) · coverage 0/25 daily (weekly opened GHSA, Ollama + Unsloth releases, arXiv cs.CR) · capture-leak 0/0 · source-discovery 0/0 (Unsloth added directly, verified)
2026-W43 — queue +4/-2 (live 5) · evidence 10, stages +2 (1 emerging→accelerating, 1 new seed) · explore 0/7 · off-axis 50% (5/10 on existing trends, 5/10 on new llm-frontend-001) · coverage 7/27 weekly-opened (0/27 via daily runs) · capture-leak 0/0 · source-discovery 0/0 (Wiz, Trail of Bits, Anthropic verified; GHSA app-layer queries added)
