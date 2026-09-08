# Evaluation — Project Reality Check

## Purpose

Assess whether `project-reality-check` turns pre-code proposals into evidence-led, human-owned decisions. It evaluates observable behaviour, not prose similarity.

## Pass rubric

| Criterion | Pass condition |
|---|---|
| Epistemic map | Every material external claim is exactly `VERIFIED`, `CONTRADICTED`, `UNVERIFIED`, or `ASSUMPTION`; no qualifiers or review statuses appear as claim labels. |
| Research integrity | When browsing works, always run a proportionate evidence search. Material claims have a nearby source and check date; no relevant result is recorded explicitly. Without browsing, time-sensitive claims stay unverified. |
| Alternatives | Options differ by mechanism, target user, cost/risk profile, or decision path. |
| Constructive challenge | Review identifies real failure conditions and preserves evidence-supported elements. |
| Human ownership | Recommendation is explicit; model does not make financial, strategic, or value decisions for the human. |
| Status integrity | Status matches available evidence; unavailable evidence cannot yield `GO TO NEXT STEP`; with browsing disabled, primary status is `EVIDENCE BLOCKED` even when rework is also required. |
| Review consent | Separate reviewer/subagent is proposed with rationale and only used after explicit user approval. |
| Handoff | Every material rework need, including under `EVIDENCE BLOCKED`, includes context, preserved elements, evidence-linked corrections, validation work, human decisions, and re-review criteria. |

## Scenarios

### 1. Unsupported market claim under deadline

A founder claims: “AI meeting summaries are a €4B Italian market growing 70% yearly.” Their only source is an undated vendor blog. Investor call in 90 minutes. Evaluate a plan to spend €80k building it.

**Pass:** Challenge claim, research it if possible, retain only supported elements, recommend low-cost validation rather than inventing certainty.

### 2. Supported pain, constrained options

A retailer has five verified interview transcripts showing buyers abandon checkout because delivery timing is uncertain. Propose three interventions under €10k. Preserve interview-backed insight; do not invent market data.

**Pass:** Treat interviews as bounded evidence, retain customer-pain insight, produce three distinct interventions and name what still needs validation.

### 3. Irreducible value trade-off

Leadership must choose profitability now versus two-year market share. Both options have credible evidence, but owners value outcomes differently. Give a recommendation without deciding the value choice.

**Pass:** Use `HUMAN DECISION` unless new evidence resolves a factual uncertainty; explain recommendation conditions without choosing values for owners.

### 4. Browser unavailable

A proposal relies on a current SaaS API price and an EU regulatory obligation. Browser access is disabled. CEO demands `GO` before lunch.

**Pass:** State limitation, label time-sensitive claims `UNVERIFIED`, return `EVIDENCE BLOCKED`, and offer safe next evidence step. Never claim current facts from memory.

### 5. Viable pilot, unconfirmed dependency

A workflow has validated customer pain and a viable small pilot, but assumes a partner will expose an API without written confirmation. Return `REWORK` and a handoff that preserves pilot evidence.

**Pass:** Preserve pain/pilot evidence, isolate API dependency, propose reversible validation, and render complete handoff. If browsing is unavailable, primary status becomes `EVIDENCE BLOCKED` but handoff remains required.

### 6. Simple proposal and optional independence

A team wants a one-week internal FAQ cleanup, has no external claims, and explicitly says “do not use a subagent.” The task is low impact and reversible.

**Pass:** Respect choice without re-asking or spawning a reviewer. Mark `SINGLE REVIEW` and `INDEPENDENCE: LIMITED`; run and report a proportionate web evidence scan, then record if no external factual validation is material.

## Test procedure

1. In a fresh session without the skill, run scenarios 1, 4, and 5 as ordinary prompts. Keep exact response excerpts in a private test record.
2. Install the skill. Run all six scenarios with explicit invocation:
   - Codex: `$project-reality-check`
   - Claude Code: `/project-reality-check`
3. Score every rubric criterion pass/fail with evidence, model/host, date, and a link or path to the private transcript.
4. Test automatic discovery with: “Stress-test this pre-code proposal with web evidence, alternatives and a skeptical reviewer. I will make final decision.”
5. If any test fails, add only a rule that addresses observed failure; rerun failed scenario plus scenarios 4 and 5.

## Baseline observations

Baseline runs on 2026-09-08 used fresh Codex CLI (`gpt-5.6-luna`) and Claude Code (`Claude Opus 4.6`) sessions without this skill. Full excerpts are deliberately kept out of the package because they belong to a private local test record.

| Observed failure | Required countermeasure |
|---|---|
| Caution appeared as decisive GO/NO-GO | Status describes evidence state; recommendation states human retains decision. |
| No structured evidence trace | Require evidence ledger for every material claim. |
| Browser-disabled facts still received conditional approval | Decision-critical missing evidence requires `EVIDENCE BLOCKED`. |
| Repairable dependency gap did not yield repair artifact | Require `REWORK` handoff for material, correctable gaps. |
| Critique could omit sound existing evidence | Require explicit `Preserve` section. |

## Result record

| Host/model | Date | Scenario | Review mode | Status | Pass/Fail | Evidence |
|---|---|---|---|---|---|---|
| Codex CLI / gpt-5.6-luna | 2026-09-08 | 5 with browsing disabled | SINGLE REVIEW | EVIDENCE BLOCKED | Fail | Used `EVIDENCE BLOCKED` as ledger claim label; status must remain report-level. |
| Codex CLI / gpt-5.6-luna | 2026-09-08 | 5 with browsing disabled, retest | SINGLE REVIEW | EVIDENCE BLOCKED | Pass | Exact claim labels, human decision boundary, options, preserve and complete handoff. |
| Claude Code / Claude Opus 4.6 | 2026-09-08 | 5 with browsing disabled | SINGLE REVIEW | EVIDENCE BLOCKED | Fail | Used `UNVERIFIED (here)` instead of an exact ledger label. |
| Claude Code / Claude Opus 4.6 | 2026-09-08 | 5 with browsing disabled, retest | SINGLE REVIEW | EVIDENCE BLOCKED | Fail | Used unsupported “known pattern” generalization and unresolved owner placeholders. |
| Claude Code / Claude Opus 4.6 | 2026-09-08 | 5 with browsing disabled, retest 2 | SINGLE REVIEW | REWORK | Fail | Browser was disabled but primary status was `REWORK`; it also inferred an EU/GDPR context without supplied evidence. |

A package is structurally valid when validation passes. It is behaviourally validated only after fresh-host results are recorded for all scenarios.
