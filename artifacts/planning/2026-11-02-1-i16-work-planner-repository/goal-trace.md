# I16 Goal Trace

The goal clauses are the user's decisions of 2 November 2026, recorded in [decisions](decisions.md). Each source requirement below is one of those decisions, or m2ux/workflow-server#1595, which decision 9 carries over whole.

## Trace Table

| Goal clause | Initiative criteria | Epics | Epic criteria | Source requirement |
| --- | --- | --- | --- | --- |
| The skill and its shared files move unchanged to prosiform-skills' root with their history | AC1 | E00 | E00 AC1, AC2, AC3, AC4 | Decisions 1, 2, 4, 6 |
| prosiform's workspace runs the skill from a pinned prosiform-skills commit, through a link | AC4 | E01 | E01 AC1, AC2, AC3, AC4, AC5 | Decisions 5, 6 |
| workflow-server's template carries no copy, and its skill files outside workflow-canon name none | AC3 | E01 | E01 AC6, AC7, AC8 | Decisions 3, 5, 8 |
| The skill's tests and the shared check pass from the new root | AC2 | E02 | E02 AC1, AC2, AC3, AC4 | Decisions 1, 6, 7 |
| Board Queue ranks by the board's Priority Number field alone | AC5 | E03 | E03 AC1, AC2, AC3, AC4, AC5, AC6 | Decision 9; #1595 AC1–AC4 |
| No `priority:` label remains | AC6 | E03 | E03 AC7 | Decisions 9, 10; #1595 AC5 |

Every epic criterion is delivered by a task row, as each epic's Coverage column shows and `format.py` reports.

## Gaps

Ranked, the first most threatening the goal.

1. **prosiform between link and removal.** prosiform's link must merge before the template's removal, or its next template update leaves it with no skill. The removal row depends on the link row; prosiform's own update timing is its owner's.
2. **Checkouts before the scripts reach them.** A prosiform checkout that pulls the link without the template's submodule checkout has an empty submodule. The link's pull request merges the template's script change first.
3. **Other forks of the template.** A workspace other than prosiform's loses work-planner at its next template update. The initiative's Non-Goals state that the template ships no work-planner.
4. **Labels before the field is read.** The label deletion depends on prosiform pinning a skill that reads the field.
5. **workflow-canon's stale command.** `skills/workflow-canon/references/revise-mode.md` still runs the check and a test suite over `skills/work-planner`, which the template no longer holds. The initiative's Non-Goals keep it.
6. **Record of where skill changes go.** md-composer's agent memory states that skill changes go to workflow-server's `workspace`. After the cutover, work-planner changes go to prosiform-skills' `main`.

## Outside Threats

- **Readers of what moves.** `deploy-workspace.sh` and `update-workspace.sh` read a workspace's tree, and each gains a submodule checkout before any workspace declares one. No hook or settings file in md-composer names the skill's path.
- **Fail-closed paths.** A missing `config/branches` leaves branch names unevaluable rather than guessed; until the branch list merges, base preparation takes the names from decision 4.
- **Baseline.** At workflow-server `785a5ee8c`, the skill's suite runs 747 tests with one skip and passes, the shared suite runs 208 and passes, and the shared check reports 0 findings over the skill's 50 files. The extraction is checked against the commit it is cut from.
- **Ground that moves.** workflow-server's `workspace` keeps moving until the extraction; the extracted commit, not `785a5ee8c`, is the comparison point.
