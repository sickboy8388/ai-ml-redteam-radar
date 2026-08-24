# Agent guide — AI-ML-RedTeam Radar

Instructions for AI agents (and humans) working in this repository. Task-specific
instructions come from the session prompt; this file holds the invariants that apply
to every session.

## What this repo is

Persistent state for **AI-ML-RedTeam Radar**, an autonomous tracker of the AI/ML security
frontier — with a center of gravity on **local and self-hosted models** (runtimes, tooling,
deployment patterns, fine-tuning, quantization) and on **offensive/defensive security of AI
systems** (jailbreaks, prompt injection, agentic attacks, model supply chain) — curated for
a red team operator working with local models. It is a RADAR (situational awareness): it
tracks and points to *published* artifacts. `TRENDS.md` is the single source of truth; the
README and reports are derived snapshots. History matters: never rewrite published history,
never force-push.

## Scope (priority order)

1. **Local & self-hosted model stack** — inference runtimes and tooling (llama.cpp, Ollama,
   vLLM, LocalAI, LM Studio, transformers), quantization formats, fine-tuning/LoRA tooling,
   RAG stacks, agent frameworks runnable on-prem; notable releases, benchmarks, and security
   issues of this stack.
1b. **AI-driven solution engineering stack (curator priority, 2026-08-24)** — beyond the
   bleeding edge, track the practical stack for BUILDING local AI-driven solutions:
   fine-tuning frameworks (Unsloth, Axolotl), efficient inference for consumer GPUs
   (ExLlama, TabbyAPI, koboldcpp), quantization advances (GGUF/AWQ/GPTQ formats), model
   releases that fit consumer hardware, embedding/vector tooling, RAG frameworks, agent
   scaffolding, evaluation tooling, and real-world build guides/benchmarks.
   **Hardware relevance filter**: the curator runs a desktop with an RTX 4070 Ti (12GB
   VRAM). Prioritize what is feasible in that envelope — typically ≤~8B dense models at
   Q4–Q8, larger MoE models via CPU/RAM offload, LoRA/QLoRA fine-tunes of ≤8B bases, and
   techniques that stretch VRAM (KV-cache quantization, speculative decoding, offload).
   Flag items that require datacenter GPUs as such instead of dropping them silently.
2. **LLM red teaming & offensive research** — jailbreak techniques, prompt/direct+indirect
   injection, agentic/tool-use abuse (MCP servers, function calling, code execution),
   multi-turn and multimodal attacks, red-team tooling (garak, PyRIT, promptfoo).
3. **AI supply chain & model security** — malicious/backdoored models on hubs (pickle &
   unsafe deserialization, weight tampering), compromised ML packages (PyPI/npm/HuggingFace),
   ML-pipeline CVEs (serving frameworks, vector DBs, orchestration).
4. **AI-assisted offense & defense** — published research on LLM-assisted phishing/malware/
   vuln-discovery, guardrails, detection evasion of AI controls, defensive tooling.
5. **Taxonomies, policy & standards** — MITRE ATLAS, OWASP LLM/GenAI Top 10, NIST AI RMF,
   EU AI Act enforcement items with technical impact, benchmark suites for model safety.

Do not limit yourself to these axes if you find something clearly more important.

## Hard rules (the constitution — never relax these)

- **Primary published sources only for EVIDENCE**, and only URLs actually opened this
  session: research labs and vendor security blogs, tool repos and their releases,
  CVEs/advisories (NVD, GHSA, vendor PSIRTs), conference material (DEF CON, Black Hat,
  USENIX Security, IEEE S&P, CCS), papers (arXiv listing pages count when opened).
  Never SEO farms, never aggregators, never paywalled re-summaries. Anything not opened is
  "unverified" → `observation_queue`.
- **Track, don't reproduce.** An evidence line is `date — primary URL — one line of context`
  (what it is, novelty, offensive/defensive impact); max 10 evidence items per trend. This
  radar points to artifacts and summarizes their significance — it is a tracker, **not a
  runbook**. Never paste operational payloads, working jailbreak strings, exploit code, or
  step-by-step attack instructions into the ledger; link the primary source instead.
- **Published/disclosed only.** Track work that is publicly released or responsibly
  disclosed. The radar does not solicit, host, or hunt for non-public exploits or live
  targets — it is field awareness, not operations against any system or organization.
- **Social carve-out (intake only):** social/community sources (r/LocalLLaMA, r/netsec, X,
  YouTube, forums, named blogs, Discord recaps) are an INTAKE LANE ONLY — they may create
  unverified `observation_queue` items (promotable only after confirmation on a primary
  artifact) and feed the community-pulse note, but NEVER become trend evidence. Never name
  individuals.
- **Access blocker ≠ quiet field.** If, after healing attempts, a run cannot open a single
  primary source (tooling missing/misconfigured, a domain systematically blocked), that is a
  blocker to log in `TRENDS.md#blockers` — not "no new trends today." If it persists across
  2+ consecutive runs, escalate to the curator (see Operator notifications below). Never
  conflate "found nothing" with "couldn't check."
- Never guess dates or invent URLs. Undated pages: "(undated, accessed YYYY-MM-DD)".
- **Trend bar:** ≥3 independent sources (different orgs/authors) + ≥1 concrete artifact
  (repo, release, CVE, paper, advisory). A single strong tool/paper is not a trend →
  `study_shelf`.
- Do not rename sections or restructure files. Everything in this repo is in English.

## File map

| Path | Contents | Edit policy |
|---|---|---|
| `TRENDS.md` | Trend ledger + `observation_queue`, `strategy_notes`, `study_shelf`, `blockers` | follow the ledger-update procedure in `routines/daily.md` |
| `SOURCES.md` | Agent-owned source registry | maintained by the radar itself |
| `README.md` | THE output surface — regenerated from the ledger on every change; never edit by hand | fully derived |
| `reports/YYYY-MM-DD.md` | Daily reports | write once, never edit old ones |
| `reports/weekly/YYYY-Wnn.md` | Weekly reports | write once |
| `logs/source_rotation.md` | Append-only daily coverage log | append-only |
| `logs/calibration.md` | Append-only weekly self-evaluation log | append-only; weekly runs only |
| `routines/*.md` | LIVE operating instructions | weekly amendments only, per the autonomy contract |

## Tooling

- Web access: use the built-in web tools (search + open/fetch). Open the actual URL of
  every artifact you cite.
- Advisories: NVD (`https://services.nvd.nist.gov/rest/json/cves/2.0`), GHSA
  (`https://github.com/advisories`), vendor PSIRT feeds, repo release feeds
  (`<repo>/releases.atom`).
- Papers: arXiv recent listings (cs.CR, cs.LG, cs.CL) and conference proceedings; open the
  abstract page before citing.
- Persistence: the repo lives at `/mnt/agents/output/ai-ml-redteam-radar` and persists
  across scheduled runs. Commit with local git (no remote is configured; if the curator
  later adds one, push to `main` per Git conventions).

## Self-amendment (autonomy contract)

The radar runs unattended: in normal operation no human edits prompts, routines, or scope.
The fixed platform prompt of each scheduled session is a fixed loader and must never change:

> You are the daily [weekly] operator of this repository. Read AGENTS.md, then read
> routines/daily.md [routines/weekly.md] and execute it exactly. If either file is missing
> or unreadable, write a report describing the problem, commit only the report, and stop.

Because `routines/*.md` hold the live operating instructions, they are amendable:

- Only WEEKLY runs amend `routines/*.md` or scope axes. Daily runs execute, never amend.
- Every amendment must cite the calibration metric or retrospective that motivates it.
- **Cooling period**: an amendment is PROPOSED in one weekly report and APPLIED on the next
  weekly run only if the motivating signal persists. Silence is consent; the curator may
  veto with a dated entry in `strategy_notes`.
- One dedicated commit per applied amendment: `radar: amend <target> — <reason>`.
- **Auto-rollback**: if calibration metrics worsen for two consecutive weeks after an
  amendment, `git revert` it and log the rollback in `logs/calibration.md`.
- Scope axes evolve the same way: a dated "radar-adopted" entry in `strategy_notes` may
  supersede an older axis. Curator entries are never deleted or edited.

**Immutable (curator-only, never self-amended):** the Hard rules, the Scope priority, this
Self-amendment section, the existence of the weekly self-evaluation step, and append-only
history.

## Git conventions

- Commit messages: `radar: daily update YYYY-MM-DD`, `radar: weekly recalibration YYYY-Wnn`.
- Any commit that changes `TRENDS.md` must regenerate `README.md` in the SAME commit.
- Never force-push, never rewrite published history. If a remote is configured, push to
  `main`; if rejected, retry once after `git pull --rebase origin main`.
- **Operator notifications**: stay silent on healthy/routine runs (a notification every run
  is noise). Flag the curator only for something they must see before the next run: a broken
  hard rule, a degradation self-flagged "heal owed" for ≥3 consecutive runs, or a
  tooling/access blocker preventing verification for 2+ consecutive runs (see Hard rules →
  Access blocker ≠ quiet field).

## Efficiency

Single-agent, one session per run. Triage then extract: read feeds/titles first, open the
full artifact only for genuinely new items. Read only the recent tail of long append-only
logs.
