## Overview

The shared skill guidelines state the rules a skill used through prosiform follows: its bootstrap, its links, its operators and its budget. Work Planner's own links, hand-offs and bootstrap are brought to these rules by the epics that follow, and the shared check enforces them once the skill conforms.

## Problem

- **The Links rules assume a reader who chooses.**
  The [shared Links rules](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/guidelines.md#L105-L118) type a selection link and a prerequisite citation, both read by an agent following links. Under prosiform every local link is a dependency, compiled whole into the bundle.
- **No rule states the bootstrap, the operators or the budget.**
  The shared guidelines name neither `pf`, nor the `⇉`, `⫽` and `¬` operators, nor a bundle's output budget.

## Proposal

- **The guidelines state the prosiform rules.**
  - A skill used through prosiform bootstraps from its entry point by running `pf` and following it.
  - A link stands where the reader must have the target's content, and names its section wherever the target carries one.
  - Prose that names another mode or file without sending the reader to it is plain text.
  - A sub-agent hand-off is `⇉`, or `⫽` for a set run together; material a step reads only in some cases is `¬`.
  - Each mode compiles within prosiform's default output budget with no warning.
- **The rules name the pinned `pf`.**
  Each rule describes the grammar of the prosiform release the repository pins.

## Work Breakdown

| Task | Description | Coverage | Depends on | Joins | Lane | Done |
| --- | --- | --- | --- | --- | --- | --- |
| [W01](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e04/w01.md) | Bootstrap and link rules stated | AC1, AC2, AC3 | [E02:W02](https://github.com/m2ux/prosiform-skills/issues/5) | W02 | | |
| [W02](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e04/w02.md) | Operator and budget rules stated | AC4, AC5 | [E02:W02](https://github.com/m2ux/prosiform-skills/issues/5) | W01 | | |

## Acceptance Criteria

- [ ] **AC1.** `guidelines.md` states that a skill used through prosiform bootstraps from its entry point by running `pf` and following it, as a read of the guidelines on `main` shows.
- [ ] **AC2.** `guidelines.md` states that a link names a section wherever its target carries a heading below its title, as a read of the guidelines' Links section on `main` shows.
- [ ] **AC3.** `guidelines.md` states that a link stands only where the reader must have its target's content, and that prose naming another mode or file otherwise is plain text, as a read of the guidelines' Links section on `main` shows.
- [ ] **AC4.** `guidelines.md` states that a sub-agent hand-off is a dispatch link and that material a step reads only in some cases is a deferral link, as a read of the guidelines' Links section on `main` shows.
- [ ] **AC5.** `guidelines.md` states that each mode of a skill used through prosiform compiles within prosiform's default output budget with no warning, as a read of the guidelines on `main` shows.

## Open Questions

- Which prosiform release, and so which grammar version, the rules name and the repository pins. It is settled before this epic starts.

## References

- **R1.** [Planning record](https://github.com/m2ux/prosiform-skills/tree/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository) — the decisions, the evidence, each Open Question and the review.
- **R2.** [Prosiform references](https://github.com/m2ux/prosiform/blob/23882b7d/docs/references.md#operators) — the three operators and what each withholds from the bundle.
- **R3.** [Prosiform validation](https://github.com/m2ux/prosiform/blob/23882b7d/docs/validation.md#budgets) — the per-bundle budgets and their failure.

🤖 Generated with [Claude Code](https://claude.com/claude-code)
