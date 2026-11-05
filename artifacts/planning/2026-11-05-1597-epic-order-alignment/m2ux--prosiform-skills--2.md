## Overview

This epic cuts the work-planner skill over to its own repository. The skill, with its history and the shared guide, rules, check and tests it is held to, moves from workflow-server's `skills/` folder to the root of prosiform-skills as it is, with no change to its content.

## Problem

The skill shares a repository with work it has nothing to do with.

- **It lives in workflow-server.**
  Its [entry point](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/work-planner/SKILL.md#L1-L5) sits beside three unrelated skills, so its history and pull requests are workflow-server's.
- **The new repository has no `main`.**
  prosiform-skills holds only its orphan `engineering` branch, which GitHub made its default branch.
- **Nothing states its branches.**
  prosiform-skills has no `config/branches`, so the skill's branch reads there report the names unevaluable.

## Proposal

- **History moves with the files.**
  `git filter-repo` keeps `skills/work-planner/`, `skills/guidelines.md`, `skills/rules.json`, `skills/scripts/check_skill_files.py` and `skills/test/test_check_skill_files.py`, and moves them up one level.
- **Content moves unchanged.**
  No file's content changes. The skill's commands still name `skills/work-planner/scripts/<name>.py`, which holds in a workspace that links the skill at `skills/work-planner`.
- **The extraction is `main`'s first history.**
  It is pushed directly, before any epic base exists, and `main` becomes the default branch. It is cut from workflow-server's `workspace` head once I17's Pre-Cutover Fixes, Skill Separation and Skill Style epics close, and its tree is compared with workflow-server's at that commit.
- **The repository states its branches.**
  `config/branches` names `main`, which task and epic pull requests target, and `engineering`, which holds planning records.

## Work Breakdown

| Task | Description | Coverage | Depends on | Joins | Lane | Done |
| --- | --- | --- | --- | --- | --- | --- |
| [W00](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e00/w00.md) | Skill history extracted into main | AC1, AC2, AC3 | [I17:E00](https://github.com/m2ux/workflow-server/issues/1598), [I17:E01](https://github.com/m2ux/workflow-server/issues/1616), [I17:E02](https://github.com/m2ux/workflow-server/issues/1615) | | | |
| [W01](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e00/w01.md) | Long-lived branches stated | AC4 | W00 | | | |

## Acceptance Criteria

- [ ] **AC1.** Each of `work-planner/`, `guidelines.md`, `rules.json`, `scripts/check_skill_files.py` and `test/test_check_skill_files.py` on prosiform-skills' `main` has the content its `skills/` counterpart has at the extracted workflow-server commit, as a `git diff` of the two trees shows.
- [ ] **AC2.** `work-planner/SKILL.md` on `main` carries the commits that changed `skills/work-planner/SKILL.md` in workflow-server up to the extracted commit, as a comparison of the two `git log --format=%s` listings shows.
- [ ] **AC3.** prosiform-skills' default branch is `main`, as `gh api repos/m2ux/prosiform-skills --jq .default_branch` shows.
- [ ] **AC4.** The long-lived branches stated on `main` are `engineering` and `main`, as `sync.py --names --revision origin/main` prints.

## References

- **R1.** [Planning record](https://github.com/m2ux/prosiform-skills/tree/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository) — the decisions, the goal trace and each task's work item.
- **R2.** [workflow-server `skills/` at the evidence revision](https://github.com/m2ux/workflow-server/tree/785a5ee8c715b802498aa41712e0489425a22cfa/skills) — the folder this epic extracts from.

🤖 Generated with [Claude Code](https://claude.com/claude-code)
