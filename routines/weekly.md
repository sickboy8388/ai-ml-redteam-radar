# AI-ML-RedTeam Radar — Weekly recalibration

You are the weekly operator of the AI-ML-RedTeam Radar repository at
`/mnt/agents/output/ai-ml-redteam-radar`. Work in English.
Compute the ISO week as YYYY-Wnn (`date +%G-W%V`).

## 1. Load state
Read `TRENDS.md`, the daily reports of the past 7 days in `reports/`, `logs/calibration.md`
(recent tail), and the previous weekly report if present.

## 2. Recalibrate every trend
Judge each trend's velocity over the last 2–3 weeks (count of new independent evidence,
breadth of orgs, presence in tools/CVEs/papers).
- **Promote** (seed → emerging → accelerating → mainstreaming) only on sustained multi-org
  evidence; one stage max per week; justify in `notes`.
- **Demote** honestly when evidence thinned.
- **Dormancy**: 21+ days without evidence → `dormant`; 45+ days → archive with a one-line
  post-mortem.
- **Merge** overlapping trends (keep older id, union aliases, keep 10 strongest evidence).
- **Confidence**: raise to `high` when ≥2 independent authoritative primary sources
  corroborate on concrete artifacts, OR after sustained multi-week confirmation; lower when
  evidence thins.
- After recalibration, regenerate `README.md` (per routines/daily.md section 6).

## 3. Clean the observation queue
Items older than 14 days — verify now and either promote, drop (one-line reason), or
re-date stating what is still missing. Hard cap ~25 live items. Curate `study_shelf`
(merge duplicates, prune picks older than 30 days).

## 4. Source strategy review
Diff every "swept every run" list in `SOURCES.md` against the week's
`logs/source_rotation.md` — every listed source must appear as `opened` or `degraded`. Any
source missing all week is a coverage lie: heal it, or propose heal-or-remove. Which
sources produced evidence, which produced nothing repeatedly? If ALL new evidence landed
on pre-existing trends, record an anchoring warning in `strategy_notes` and redirect
exploration.
**Source discovery (drain the staged candidates):** review `SOURCES.md → Discovered-source
candidates`. For each org/domain at the promotion bar (≥2 on-axis primaries, OR recurrence
across ≥2 runs), VERIFY by opening its feed/repo/channel; if it is a real on-axis primary
source, PROMOTE it into the matching swept list as `[verified YYYY-MM-DD]` and clear its
staging line; drop one-off noise with a one-line reason.

## 5. Self-evaluation
Compute the metric set below and append one dated line to `logs/calibration.md` (every
metric present, even at 0). Format:

    YYYY-Wnn — queue +A/-D (live L) · evidence E, stages +S · explore X/7 · off-axis P% · coverage s/t · capture-leak n/m · source-discovery s/p

- queue: items added/dropped this week, live count
- evidence: new evidence lines appended; stage changes
- explore: of the 7 daily exploration slots, how many ran
- off-axis: % of new evidence that landed on pre-existing trends vs new ones
- coverage: sources opened / total swept-listed
- capture-leak: items that should have been queued but were claimed without verification
- source-discovery: candidates staged / promoted

Once a month (first weekly run of the month), add a short retrospective: what the radar
missed, what it over-tracked, whether the local-model axis is getting enough depth.

## 6. Self-amendment (per the autonomy contract in AGENTS.md)
- APPLY amendments proposed in LAST week's report whose motivating signal PERSISTS and
  that carry no dated curator veto in `strategy_notes`. One dedicated commit each
  (`radar: amend <target> — <reason>`), citing the metric that motivates it.
- Check amendments applied 1–2 weeks ago for regression: if calibration worsened for two
  consecutive weeks after one, `git revert` it and log the rollback in
  `logs/calibration.md`.
- Write THIS week's new proposals (≤3, each citing a metric/retrospective) under
  "Amendments — proposed" in the report. They apply next week only if the signal persists.
- Never touch the immutable sections of AGENTS.md.

## 7. Write the weekly report
Create `reports/weekly/YYYY-Wnn.md` (under ~90 lines): stage moves/merges/archivals;
strongest & weakest trend; 3–5 forward-looking bets; source strategy changes; calibration
block (+ monthly retrospective when due); amendments applied / proposed / rolled back.

## 8. Persist
`git add -A` && commit `radar: weekly recalibration YYYY-Wnn` (local repo; push to `main`
only if a remote is configured — if rejected, retry once after `git pull --rebase`).
Never force-push, never rewrite published history.
