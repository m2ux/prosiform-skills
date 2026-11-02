# I16 Goal Trace

The goal clauses are the user's decisions of 2 November 2026, recorded in [decisions](decisions.md). Each source requirement below is one of those decisions, or m2ux/workflow-server#1595, which decision 6 carries over whole.

## Trace Table

| Goal clause | Initiative criteria | Epics | Epic criteria | Source requirement |
| --- | --- | --- | --- | --- |
| The skill and its shared files live at prosiform-skills' root with their history | AC1 | E00 | E00 AC1, AC2, AC3 | Decisions 1, 2 |
| The skill works from its new root, planned on `engineering` and delivered into `main` | AC2 | E00 | E00 AC4, AC5, AC6, AC7, AC8 | Decisions 1, 4; open-point decision 1 |
| workflow-server's template carries no plain copy, and its shared files outside workflow-canon name none | AC3 | E01 | E01 AC6, AC7, AC8 | Decision 3; open-point decisions 2, 5 |
| Workspaces made or updated from the template install the skill from a pinned prosiform-skills commit | AC4 | E01 | E01 AC1, AC2, AC3, AC4, AC5 | Decision 5; open-point decision 3 |
| Board Queue ranks by the board's Priority Number field alone | AC5 | E02 | E02 AC1, AC2, AC3, AC4, AC5, AC6 | Decision 6; #1595 AC1–AC4 |
| No `priority:` label remains | AC6 | E02 | E02 AC7 | Decision 6; #1595 AC5; open-point decision 4 |

Every epic criterion is delivered by a task row, as each epic's Coverage column shows and `format.py` reports.

## Gaps

Ranked, the first most threatening the goal.

1. **Forks behind the template.** A workspace that has not run `update-workspace.sh` since the submodule landed still runs its plain copy, which reads priority labels. Deleting the labels empties that copy's queue until it updates. The label row follows the template's pin move; each fork's own update stays its owner's to run.
2. **Labels before the field is read.** The label deletion depends on the template pinning a skill that reads the field, and the template's plain copy is gone before the field work starts.
3. **workflow-canon's stale command.** `skills/workflow-canon/references/revise-mode.md` still runs the check and a test suite over `skills/work-planner`, which then reaches the submodule's copy through the link. The initiative's Non-Goals keep it.
4. **Record of where skill changes go.** md-composer's agent memory states that skill changes go to workflow-server's `workspace`. After the migration, work-planner changes go to prosiform-skills' `main`.

## Outside Threats

- **Readers of what moves.** `deploy-workspace.sh` and `update-workspace.sh` read the template's `skills/`, and each gains a submodule checkout before the template carries a submodule. No hook or settings file in md-composer names the skill's path.
- **Fail-closed paths.** A missing `config/branches` leaves branch names unevaluable rather than guessed; until the branch list merges, base preparation takes the names from decision 4.
- **Baseline.** At workflow-server `785a5ee8c`, the skill's suite runs 747 tests with one skip and passes, the shared suite runs 208 and passes, and the shared check reports 0 findings over the skill's 50 files. The extraction is checked against the commit it is cut from.
- **Ground that moves.** workflow-server's `workspace` keeps moving until the extraction; the extracted commit, not `785a5ee8c`, is the comparison point.
