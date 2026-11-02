# I16 Prosiform Evidence

Measurements behind the Problem sections of E04 to E07. Every figure names the revision and instrument that produced it. Paths are workflow-server's, where the skill stood when measured.

## Revisions

| Name | Revision | Note |
| --- | --- | --- |
| Head | workflow-server `785a5ee8c` (origin/workspace, 2026-11-02) | The evidence revision; the extraction is cut from workflow-server's `workspace` head once I17's Pre-Cutover Fixes epic closes. Exported with `git archive` and measured there. |
| Baseline candidate in md-composer | md-composer `93dad5b9` | Not an object in workflow-server. Its second parent is workflow-server `ed508443`, an ancestor of head. |
| Baseline candidate in workflow-server | `ed508443` | Work Planner markdown identical to md-composer `93dad5b9`; only `test/test_modes.py` differs. |

## Instrument

- `pf -v` reports `pf 0.12.0 (skill-markdown-v1)`, installed at `~/.local/bin/pf`.
- Prosiform's README at m2ux/prosiform `23882b7d` names profile `skill-markdown-v4`; its source declares version 0.16.0 and `PROFILE = "skill-markdown-v4"`.
- The latest release tags are `contract/v0.15.0` and `python/v0.15.0`, whose source declares `skill-markdown-v3`.
- The installed 0.12.0 prints no guide when run bare (`E_INVALID_USAGE: at least one entry reference is required`) and takes `-o FILE`; the README describes a guide printed by bare `pf`, the `↳` link form, and a bundle folder per run.
- Default output budget (`pf -h`): `-O 262144`.

## Bundle Sizes

Command, from the exported tree's root: `pf skills/work-planner/modes/<mode>-mode.md -O 4000000 -o <file>`, pf 0.12.0. No run printed a diagnostic.

| Mode | Head `785a5ee8c` | Baseline candidate `ed508443` | Over 262144 at head |
| --- | --- | --- | --- |
| deliver | 353717 | 352872 | yes |
| plan | 328950 | 323049 | yes |
| advance | 314874 | 309165 | yes |
| standup | 273929 | 268030 | yes |
| sync | 264276 | 258377 | yes |
| hoist | 239774 | 234050 | no |
| align | 215401 | 209675 | no |
| understand | 119382 | 119382 | no |
| revise | 65816 | 65816 | no |
| propose | 56661 | 56661 | no |
| SKILL.md | 405673 | 404832 | yes |

At `ed508443` four modes exceed the budget, Sync falling under it.

## Links

Counted at head by a script reading every Work Planner markdown file outside fenced blocks and code spans:

- 1075 internal links; 245 name a whole file, and every one of those targets carries a heading below its title.
- 25 whole-file links name a mode file: 10 in SKILL.md's Modes list, the rest in mode Prerequisites and steps of Advance, Deliver, Plan, Standup and Sync.
- 0 links carry a `¬`, `⇉` or `⫽` operator.

## Check Callers

- `skills/work-planner/modes/revise-mode.md` lines 78 to 98 run the shared check over a skill directory.
- Three Work Planner tests import the check module: `test_worktrees.py`, `test_documents.py`, `test_checkouts.py`.
- workflow-canon's `references/revise-mode.md` lines 72 to 73 also run workflow-server's copy of the check; that copy stays in workflow-server, as decision 3 states, and takes none of these findings.

## Bare Check Paths

At head, the only prose naming a check script by a code span is `skills/guidelines.md` line 198. Two further code spans name a `.py` file as an example rather than a check: Work Planner `guidelines.md` line 175 and `artifacts/work-item.md` line 62.
