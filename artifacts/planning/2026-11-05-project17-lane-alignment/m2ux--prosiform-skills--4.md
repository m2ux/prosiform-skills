## Overview

An epic's or initiative's priority is a number in its board's Priority field. Board Queue reads that field and no label, and the `priority:` labels are gone.

## Problem

- **Priority has two homes.**
  Board Queue ranks by `priority: <n>` labels, through its [`RANK` pattern](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/work-planner/scripts/board-queue.py#L33). Board 17's Priority field is a single-select of High, Medium and Low that nothing reads.
- **Labels that look like priorities don't rank.**
  workflow-server carries `priority: highest`, `high`, `medium`, `low` and `lowest`. Board Queue reads only numbered labels, so those issues have no priority.
- **The field can't hold a rank.**
  Three options can't express the numbered sets Board Queue runs, where the highest number runs together and the next waits in Ready.
- **Planning writes labels.**
  Plan mode [saves each confirmed number](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/work-planner/modes/plan-mode.md#L72) as the epic's priority label.

## Proposal

- **Priority is a Number field.**
  Every theme board, and the Initiative template, has a Number field named Priority in place of the single-select. A larger number runs first. An empty value means no priority, and that epic never starts.
- **Board Queue reads the field.**
  `board-queue.py`, and every other script and rule that reads or sets a priority, use the board item's Priority field. No script or rule names a priority label.
- **Numbered labels move across, then every priority label goes.**
  Each open issue's `priority: <n>` becomes its board item's Priority value, unchanged. Word labels move nothing across.
- **Order of change.**
  The field values are set before the skill change merges. The labels are deleted only once prosiform's workspace pins a skill that reads the field, so every queue always has one source.

## Work Breakdown

| Task | Description | Coverage | Depends on | Joins | Lane | Done |
| --- | --- | --- | --- | --- | --- | --- |
| [W01](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e03/w01.md) | Priority Number field on every board | AC1, AC2 | [E00:W01](https://github.com/m2ux/prosiform-skills/issues/2), [E01:W04](https://github.com/m2ux/prosiform-skills/issues/3) | | | |
| [W02](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e03/w02.md) | Board Queue reads the Priority field | AC3, AC4 | W01 | W03 | | |
| [W03](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e03/w03.md) | Planning sets the Priority field | AC5 | W01 | W02 | | |
| [W04](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e03/w04.md) | prosiform pins a skill reading the field | AC6 | W02, W03 | | | |
| [W05](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e03/w05.md) | Priority labels deleted | AC7 | W04 | | | |

## Acceptance Criteria

- [ ] **AC1.** Every open theme board and the Initiative template has a Number field named Priority and no Priority single-select, as a field listing of each board shows.
- [ ] **AC2.** Each open issue that carried `priority: <n>` has Priority `<n>` on its board item, as the listing recorded before the move and the listing after it show.
- [ ] **AC3.** Board Queue ranks an epic by its board item's Priority number, with the larger number running first, as a `board-queue.py` test over board items with no priority labels shows.
- [ ] **AC4.** An epic whose Priority field is empty stays in Backlog and is reported as waiting on a priority, as a `board-queue.py` test shows.
- [ ] **AC5.** No work-planner script, artifact or mode reads, sets or names a priority label, as `git grep -n -i -e 'priority label' -e 'priority: *[<0-9]' -- work-planner` shows.
- [ ] **AC6.** prosiform's `workspace` pins prosiform-skills at a commit whose skill names no priority label, as `git submodule status` and the same grep at that commit show.
- [ ] **AC7.** No repository whose issues an open theme board holds carries a `priority:` label, as the before-and-after label listing in the planning record shows.

## References

- **R1.** [Planning record](https://github.com/m2ux/prosiform-skills/tree/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository) — the decisions, the goal trace and each task's work item.
- **R2.** [Board Queue](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/work-planner/artifacts/board-queue.md#L35-L57) — the queue rules the priority feeds.
- **R3.** [m2ux/workflow-server#1595](https://github.com/m2ux/workflow-server/issues/1595) — the issue this epic carries over.
- **R4.** [m2ux/workflow-server#1591](https://github.com/m2ux/workflow-server/issues/1591) — no priority means no start.

🤖 Generated with [Claude Code](https://claude.com/claude-code)
