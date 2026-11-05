## Overview

Work Planner is used through prosiform. Its entry point tells the reader to run `pf` and follow it, every mode compiles within the default output budget with no warning, and each mode's bundle size is compared against a fixed baseline revision. Once the skill's files conform, the shared skill-file check gains its prosiform findings, so a later change that breaks a prosiform rule in any skill it runs over draws a finding.

## Problem

- **The entry point is read, not compiled.**
  [SKILL.md](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/work-planner/SKILL.md#L19-L67) selects a mode by a link the reader follows; compiling SKILL.md itself yields a 405673-byte bundle carrying every mode.
- **Five modes overflow the default budget.**
  At [785a5ee8c](https://github.com/m2ux/workflow-server/tree/785a5ee8c715b802498aa41712e0489425a22cfa/skills/work-planner): Deliver 353717 bytes, Plan 328950, Advance 314874, Standup 273929 and Sync 264276, against 262144.
- **Nothing fixes what a change costs.**
  No record holds each mode's bundle size, so a change that grows a bundle is seen only when it crosses the budget.
- **The check reads resolution only.**
  The [shared skill-file check](https://github.com/m2ux/workflow-server/blob/785a5ee8c715b802498aa41712e0489425a22cfa/skills/scripts/check_skill_files.py#L1025-L1029) confirms that a link resolves; a whole-file link to a file with sections, a mode linking another mode whole, and a mode that overflows the budget all pass.

## Proposal

- **SKILL.md bootstraps through `pf`.**
  The entry point's one instruction is to run `pf` and follow it, and its Modes list selects a mode through a link prosiform compiles.
- **Each mode fits its bundle.**
  A mode still over the budget once its links carry prosiform's meaning is cut to its own procedure, moving a section only some steps use to a file of its own.
- **One comparison fixes the cost.**
  Each mode's bundle at the settled revision is compared with its bundle at the baseline revision, compiled by one prosiform version on both.
- **The check enforces the prosiform rules over every skill it runs over.**
  It reports a whole-file link to a target with sections, a mode or protocol reaching a mode file without an operator, and a mode whose compilation crosses the budget or warns. A missing or mismatched `pf` is a finding, never a skip.
- **The findings land after the skill conforms.**
  The check gains them last, so no branch carries a finding against the skill's own files.

## Work Breakdown

| Task | Description | Coverage | Depends on | Joins | Lane | Done |
| --- | --- | --- | --- | --- | --- | --- |
| [W01](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e07/w01.md) | Entry point bootstraps through prosiform | AC1 | [E06:W03](https://github.com/m2ux/prosiform-skills/issues/8) | | | |
| [W02](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e07/w02.md) | Every mode compiled within budget | AC2 | [E06:W03](https://github.com/m2ux/prosiform-skills/issues/8) | | | |
| [W03](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e07/w03.md) | Bundle sizes compared against baseline | AC3 | W01, W02 | | | |
| [W04](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e07/w04.md) | Check reports link scope and mode reach | AC4, AC5 | W01, W02, [E05:W03](https://github.com/m2ux/prosiform-skills/issues/7) | W05 | | |
| [W05](https://github.com/m2ux/prosiform-skills/blob/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository/e07/w05.md) | Check compiles each mode under budget | AC6, AC7, AC8 | W01, W02, [E05:W03](https://github.com/m2ux/prosiform-skills/issues/7) | W04 | | |

## Acceptance Criteria

- [ ] **AC1.** A session given a Work Planner request runs `pf` from the entry point and follows the bundle of the mode it selects, as a walk of a representative request from the entry point records.
- [ ] **AC2.** Every Work Planner mode on `main` compiles under the pinned `pf` within its default output budget with no warning, as each mode's compile recorded in the planning record shows.
- [ ] **AC3.** No Work Planner mode's bundle is larger than at the baseline revision the planning record fixes, as the bundle-size comparison records using one prosiform version on both revisions.
- [ ] **AC4.** The shared skill-file check reports a link naming no heading where its target carries one below its title, and none where the target carries no such heading, as `python3 -m unittest discover -s test` run from the repository root shows against a specimen skill carrying each.
- [ ] **AC5.** The shared skill-file check reports a mode or protocol file that reaches a mode file through a link carrying no operator, as `python3 -m unittest discover -s test` shows against a specimen skill carrying that link and one carrying a dispatch.
- [ ] **AC6.** The shared skill-file check reports each mode whose compilation under prosiform exceeds the default output budget or warns, as `python3 -m unittest discover -s test` shows against a specimen skill carrying an oversized mode and a warning mode.
- [ ] **AC7.** The shared skill-file check reports an absent `pf`, or one whose profile differs from the profile the check names, as a finding rather than skipping the compile, as `python3 -m unittest discover -s test` shows.
- [ ] **AC8.** The shared skill-file check, its prosiform findings included, reports no finding over `work-planner` on `main`, as `python3 scripts/check_skill_files.py work-planner` run from the repository root shows.

## Open Questions

- Which prosiform release, and so which grammar version, the check names and the comparison compiles with. It is settled before this epic starts.
- Which revision is the baseline: the extraction commit on prosiform-skills' `main`, cut from workflow-server's `workspace` head once I17's Pre-Cutover Fixes epic closes, or workflow-server `ed508443`, whose Work Planner markdown matches md-composer `93dad5b9`. It is settled before this epic starts.

## References

- **R1.** [Planning record](https://github.com/m2ux/prosiform-skills/tree/engineering/artifacts/planning/2026-11-02-1-i16-work-planner-repository) — the bundle measurements at each candidate baseline, the walk, the comparison and the review.
- **R2.** [Prosiform usage](https://github.com/m2ux/prosiform/blob/23882b7d/README.md#usage) — the guide `pf` prints and the bootstrap it states.
- **R3.** [Prosiform validation](https://github.com/m2ux/prosiform/blob/23882b7d/docs/validation.md#budgets) — the per-bundle budgets and their failure.

🤖 Generated with [Claude Code](https://claude.com/claude-code)
