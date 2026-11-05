## Overview

This epic links the work-planner skill into the workspace that uses it. prosiform's workspace takes the skill from a prosiform-skills submodule pinned to a commit, workflow-server's `workspace` template supports that vendor pattern without vendoring the skill itself, and the template's plain copy goes.

## Problem

The skill reaches its workspace as a copy, and the template's scripts know no other way.

- **A copy, not a version.**
  workflow-server's template holds [`skills/work-planner`](https://github.com/m2ux/workflow-server/tree/785a5ee8c715b802498aa41712e0489425a22cfa/skills/work-planner) as plain files. prosiform's workspace takes them through template updates, and nothing records which skill commit it runs.
- **Deploy skips submodules.**
  `deploy-workspace.sh` [clones the workspace branch](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/scripts/deploy-workspace.sh#L85-L86) without its submodules.
- **Update skips submodules.**
  `update-workspace.sh` [merges the template](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/scripts/update-workspace.sh#L31-L33) and leaves any submodule as it was.
- **The shared check names the copy.**
  The check's [usage](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/scripts/check_skill_files.py#L79-L80) and a [guide example](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/guidelines.md#L140) name `work-planner` under `skills/`.

## Proposal

- **Skills belong to each workspace.**
  The template declares no prosiform-skills submodule. A workspace that uses a skill from another repository vendors it under `vendor/` and links it into `skills/`.
- **The template's scripts support the vendor pattern.**
  `deploy-workspace.sh` and `update-workspace.sh` check out whatever submodules a workspace declares, at their pinned commits.
- **prosiform's workspace links the skill.**
  It first takes the template's script change, then adds prosiform-skills as a full submodule at `vendor/prosiform-skills`, with no sparse checkout, pinned to a commit on `main`. `skills/work-planner` becomes a tracked symlink to `../vendor/prosiform-skills/work-planner`, so the skill runs unchanged.
- **The template's copy goes after the link.**
  The template deletes `skills/work-planner` only once prosiform's link has merged, so prosiform never has neither copy.
- **The removal merges cleanly into prosiform.**
  At prosiform's next template update, both sides have deleted the plain files and only prosiform's side holds the symlink, so the merge keeps the symlink with no conflict.
- **workflow-canon is left as it stands.**
  Its `references/revise-mode.md` still names `skills/work-planner`.

## Work Breakdown

| Task | Description | Coverage | Depends on | Joins | Lane | Done |
| --- | --- | --- | --- | --- | --- | --- |
| [W01](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e01/w01.md) | Deploy checks out submodules | AC1 | | | | |
| [W02](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e01/w02.md) | Update checks out submodules | AC2 | | | | |
| [W03](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e01/w03.md) | prosiform workspace links the skill | AC3, AC4, AC5 | W01, W02, [E00:W00](https://github.com/m2ux/prosiform-skills/issues/2) | | | |
| [W04](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e01/w04.md) | Plain copy removed from the template | AC6, AC7, AC8 | W03 | | | |

## Acceptance Criteria

- [ ] **AC1.** `deploy-workspace.sh` makes a workspace whose submodules stand at the commits that workspace pins, as a deploy from a fixture workspace carrying a submodule shows.
- [ ] **AC2.** `update-workspace.sh` leaves a workspace's submodules at the commits it pins after the template merges in, as an update of a fixture fork whose submodule pin moves shows.
- [ ] **AC3.** prosiform's `workspace` has a full prosiform-skills submodule at `vendor/prosiform-skills`, pinned to a commit that prosiform-skills' `main` contains, as `git submodule status` and `git branch -r --contains` of the pinned commit show.
- [ ] **AC4.** prosiform's `skills/work-planner` is a tracked symlink to `../vendor/prosiform-skills/work-planner`, as `git ls-tree` of its `workspace` shows.
- [ ] **AC5.** The skill's test suite passes run through `skills/work-planner` in a fresh clone of prosiform's `workspace` with its submodules, as `python3 -m unittest discover -s skills/work-planner/test` there shows.
- [ ] **AC6.** workflow-server's `workspace` template tracks no file under `skills/work-planner/`, as `git ls-tree -r` of its head shows.
- [ ] **AC7.** No file under the template's `skills/` outside `skills/workflow-canon` names work-planner, as `git grep -n work-planner -- skills ':!skills/workflow-canon'` shows.
- [ ] **AC8.** workflow-server's shared test suite passes on `workspace`, as `python3 -m unittest discover -s skills/test` shows.

## References

- **R1.** [Planning record](https://github.com/m2ux/prosiform-skills/tree/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository) — the decisions, the goal trace and each task's work item.

🤖 Generated with [Claude Code](https://claude.com/claude-code)
