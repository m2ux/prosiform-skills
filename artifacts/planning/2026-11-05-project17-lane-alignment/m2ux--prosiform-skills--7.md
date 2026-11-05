## Overview

The shared skill guidelines define each check prosiform-skills runs: what it decides, which skills it binds, how it is run and where its tests live. Prose names a check by linking to its definition, and the shared skill-file check reports a check named by its bare path.

## Problem

- **A check is named by its path.**
  The shared guidelines' [Verified rule](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/guidelines.md#L198) names the shared check as a code span, so the reader meets a file path rather than a check with a purpose.
- **No check is defined.**
  The [Files rule](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/guidelines.md#L27-L28) says where shared and per-skill checks sit, and nothing says what any of them decides, which skills it binds, how it is run, or where its tests live.
- **Nothing reports a bare path.**
  The [shared skill-file check](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/scripts/check_skill_files.py#L1025-L1029) treats a code span as specimen text and reads nothing in it.

## Proposal

- **The shared guide has a Checks section.**
  One entry per check prosiform-skills runs, stating what it decides, which skills it binds, how it is run and where its tests live.
- **Prose links the definition.**
  A sentence naming a check links its Checks entry, as a command is named by linking its specification.
- **The check reports a bare path.**
  A code span naming the script of a check the Checks section defines is a finding, in every skill the check runs over. It lands once the prose it reads names each check by link.

## Work Breakdown

| Task | Description | Coverage | Depends on | Joins | Lane | Done |
| --- | --- | --- | --- | --- | --- | --- |
| [W01](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e05/w01.md) | Each check defined in the shared guide | AC1 | [E02:W02](https://github.com/m2ux/prosiform-skills/issues/5) | | | |
| [W02](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e05/w02.md) | Prose names each check by link | AC2 | W01, [E02:W01](https://github.com/m2ux/prosiform-skills/issues/5) | | | |
| [W03](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e05/w03.md) | Check reports a check named by path | AC3, AC4 | W02 | | | |

## Acceptance Criteria

- [ ] **AC1.** `guidelines.md` defines each check prosiform-skills runs — what it decides, which skills it binds, how it is run and where its tests live — as a read of its Checks section on `main` against the repository's check scripts shows.
- [ ] **AC2.** No file under `work-planner/` and no shared file names a defined check by a bare path, as a `git grep` of the check scripts' names over `work-planner` and `guidelines.md` on `main` shows.
- [ ] **AC3.** The shared skill-file check reports a code span naming the script of a check `guidelines.md` defines, as `python3 -m unittest discover -s test` run from the repository root shows against a specimen skill carrying that span.
- [ ] **AC4.** The shared skill-file check reports no bare check path over `work-planner` on `main`, as `python3 scripts/check_skill_files.py work-planner` run from the repository root shows.

## References

- **R1.** [Planning record](https://github.com/m2ux/prosiform-skills/tree/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository) — the decisions, the check inventory and the review.

🤖 Generated with [Claude Code](https://claude.com/claude-code)
