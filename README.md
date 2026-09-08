# Project Reality Check

**Evidence-led pre-code decisions for AI agents.**

AI planning sessions can produce plausible agreement while leaving weak assumptions, missing evidence, and better alternatives unexamined.

Once an idea turns into code, budget, or a public commitment, correcting those gaps becomes slower and more expensive.

Project Reality Check is a research-first review skill that pressure-tests project ideas, strategies, product concepts, and business cases before that point. It separates evidence from assumptions, surfaces counterarguments, and proposes viable alternatives. It gives advice; you make the decision.

Built for **Claude Code**, **Codex**, and other agents that can load a Markdown skill.

## Why use it?

A good review should:

- Research material external claims when web access exists.
- Separate verified facts, contradictions, unknowns, and assumptions.
- Preserve what is supported; challenge what is not.
- Compare materially different options, not cosmetic variants.
- Make the decision boundary explicit: the human decides.
- Ask before using a separate reviewer or subagent. It is never started automatically.

## What it does not do

It does not guarantee that a project will succeed, replace domain experts, invent missing research, or make strategic, financial, legal, ethical, or priority choices for you.

If browsing or decisive evidence is unavailable, it says so and uses the review-level status `EVIDENCE BLOCKED`. It does not turn its memory into a citation.

## Install

Download or clone this repository:

```bash
git clone https://github.com/DarthGit84/project-reality-check.git
cd project-reality-check
```

### Claude Code

```bash
mkdir -p ~/.claude/skills/project-reality-check
cp SKILL.md ~/.claude/skills/project-reality-check/SKILL.md
```

Restart Claude Code if the new command does not appear. Then use:

```text
/project-reality-check
Evaluate this proposal before we commit to implementation: ...
```

### Codex

```bash
mkdir -p ~/.agents/skills/project-reality-check
cp SKILL.md ~/.agents/skills/project-reality-check/SKILL.md
```

Restart Codex if it has not detected the local skill. Then use:

```text
$project-reality-check
Evaluate this proposal before we commit to implementation: ...
```

For repository-local use, place the same folder under `.claude/skills/project-reality-check/` for Claude Code or `.agents/skills/project-reality-check/` for Codex.

## What a review produces

The output follows a stable decision package:

| Part | Purpose |
|---|---|
| Decision and boundaries | Defines the actual human decision, constraints, success, and time horizon. |
| Evidence ledger | Labels every material external claim as `VERIFIED`, `CONTRADICTED`, `UNVERIFIED`, or `ASSUMPTION`. |
| Options | Compares at least three meaningfully different paths when they exist. |
| Constructive red team | Tests causal gaps, failure modes, counter-evidence, and second-order effects. |
| Preserve | Keeps the parts the evidence still supports. |
| Recommendation and status | Gives conditional advice, never a decision on the human’s behalf. |
| Rework handoff | Supplies a reusable Markdown correction brief whenever material rework is needed. |

The skill always frames the work with Blue, White, and Black thinking lenses. It adds Green, Yellow, Red, inversion, pre-mortem, systems, scenarios, or TRIZ only when the proposal needs them.

## Reviewer choice stays yours

For a simple, reversible proposal, the skill recommends a `SINGLE REVIEW` and discloses `INDEPENDENCE: LIMITED`.

For high stakes, uncertainty, conflicting evidence, irreversible cost, or significant dependencies, it recommends an `INDEPENDENT REVIEW` — but asks first. If you decline, or your host cannot start another agent, it does not pretend a single model is independent.

## Evaluation and limits

See [EVALUATION.md](EVALUATION.md) for six behavior-based scenarios, a pass rubric, and recorded observations. A structural check only verifies that the package is well formed; it does not prove model behavior. Please report reproducible results, including failures.

## Contributing

Issues are welcome for:

- behavior that violates the stated rules;
- a reproducible evaluation result;
- an evidence-backed improvement;
- clearer installation documentation;
- a proposed scenario that reveals a meaningful failure mode.

Read [CONTRIBUTING.md](CONTRIBUTING.md) before opening an issue or pull request. Do not paste customer data, credentials, private repositories, or confidential prompts.

## License

[MIT](LICENSE).

**Keywords:** Claude Code skill, Codex skill, AI agents, agent skills, brainstorming, project planning, decision making, evidence-led review, adversarial review.
