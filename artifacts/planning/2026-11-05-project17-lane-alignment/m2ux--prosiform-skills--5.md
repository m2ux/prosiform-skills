## Overview

This epic fits the work-planner skill to its own repository once the cutover and the workspace link are done. Its commands name their scripts relative to the skill, and the shared check and its tests run from the repository's root.

## Problem

The skill and its shared check still assume the `skills/` folder they came from.

- **Commands name the host's layout.**
  71 occurrences of `skills/work-planner` in 22 of the skill's files, such as the [format check](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/work-planner/artifacts/issue-body.md#L226), hold only where the skill sits under a `skills/` folder.
- **A test reads that layout.**
  `test_documents.py` finds the scripts a command runs by matching [that same path](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/work-planner/test/test_documents.py#L155).
- **The shared check assumes that folder.**
  The check's [usage](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/scripts/check_skill_files.py#L79-L80) runs it as `skills/scripts/check_skill_files.py` over `skills/work-planner`.

## Proposal

- **Scripts are named relative to the skill.**
  A command names its script relative to `SKILL.md`, as `scripts/<name>.py`, and every procedure runs from the skill's folder. `<workspace>` still supplies `scripts/sbx`.
- **The shared check runs from the root.**
  Its usage, its tests and the guide's examples name the root layout.
- **Workspaces take the change by pin.**
  A workspace runs the refactored skill once it moves its submodule pin to a commit holding it.

## Work Breakdown

| Task | Description | Coverage | Depends on | Joins | Lane | Done |
| --- | --- | --- | --- | --- | --- | --- |
| [W01](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e02/w01.md) | Scripts named relative to the skill | AC1, AC2 | [E00:W01](https://github.com/m2ux/prosiform-skills/issues/2), [E01:W04](https://github.com/m2ux/prosiform-skills/issues/3) | | | |
| [W02](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e02/w02.md) | Shared check run from the root | AC3, AC4 | [E00:W01](https://github.com/m2ux/prosiform-skills/issues/2), [E01:W04](https://github.com/m2ux/prosiform-skills/issues/3) | | | |

## Acceptance Criteria

- [ ] **AC1.** Every command specification in the skill runs its script as `scripts/<name>.py` from the skill's folder, as `test_documents.py`'s cited-command test and `git grep -n skills/work-planner -- work-planner ':!work-planner/test'` show.
- [ ] **AC2.** The skill's test suite passes on `main`, as `python3 -m unittest discover -s work-planner/test` run from the repository root shows.
- [ ] **AC3.** The shared check reports no finding over `work-planner` on `main`, as `python3 scripts/check_skill_files.py work-planner` run from the repository root shows.
- [ ] **AC4.** The shared test suite passes on `main`, as `python3 -m unittest discover -s test` run from the repository root shows.

## References

- **R1.** [Planning record](https://github.com/m2ux/prosiform-skills/tree/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository) — the decisions, the goal trace and each task's work item.

🤖 Generated with [Claude Code](https://claude.com/claude-code)
