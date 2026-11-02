# I16 Goal Trace

The goal clauses are the user's decisions of 2 November 2026, recorded in [decisions](decisions.md). Each source requirement below is one of those decisions, or m2ux/workflow-server#1595, which decision 6 carries over whole.

## Trace Table

| Goal clause | Initiative criteria | Epics | Epic criteria | Source requirement |
| --- | --- | --- | --- | --- |
| The skill and its shared files live at prosiform-skills' root with their history | AC1 | E00 | E00 AC1, AC2, AC3 | Decisions 1, 2 |
| The skill works from its new root, planned on `engineering` and delivered into `main` | AC2 | E00 | E00 AC4, AC5, AC6, AC7, AC8 | Decisions 1, 4 |
| workflow-server carries no copy, and its shared check and tests name none | AC3 | E00 | E00 AC9, AC10, AC11 | Decision 3 |
| md-composer installs the skill from a pinned prosiform-skills commit | AC4 | E01 | E01 AC1, AC2, AC3 | Decision 5 |
| Board Queue ranks by the board's Priority Number field alone | AC5 | E02 | E02 AC1, AC2, AC3, AC4, AC5, AC6 | Decision 6; #1595 AC1–AC4 |
| No `priority:` label remains | AC6 | E02 | E02 AC7 | Decision 6; #1595 AC5 |

Every epic criterion is delivered by a task row, as each epic's Coverage column shows and `format.py` reports.

## Gaps

Ranked, the first most threatening the goal.

1. **md-composer's merge window.** Between workflow-server deleting the skill and md-composer adding its submodule, a routine merge of workflow-server's `workspace` into md-composer deletes the installed skill. The submodule task takes that merge itself, so md-composer merges nothing from workflow-server's `workspace` between the two. Flagged.
2. **Command paths across installs.** The skill's commands name a host-relative path. The epic's open question settles the form; until it does, the path task cannot start. Flagged.
3. **Deployed workspaces.** workflow-server's `scripts/deploy-workspace.sh` copies `skills/` into each workspace it deploys, so a workspace deployed after the deletion has no work-planner. The initiative's Non-Goals keep installs other than md-composer out of scope.
4. **Labels before the field is read.** Deleting the labels while a copy still reads them empties that copy's queue. The label deletion depends on md-composer's pin moving to a skill that reads the field, and workflow-server's copy is gone before the field work starts.
5. **Record of where skill changes go.** md-composer's agent memory states that skill changes go to workflow-server's `workspace`. After the migration, work-planner changes go to prosiform-skills' `main`.

## Outside Threats

- **Readers of what moves.** md-composer's `.claude/skills` and workflow-server's `deploy-workspace.sh` read `skills/work-planner`; both are named above. No hook or settings file in md-composer names the skill's path.
- **Fail-closed paths.** A missing `config/branches` leaves branch names unevaluable rather than guessed; until the branch list merges, base preparation takes the names from decision 4.
- **Baseline.** At workflow-server `785a5ee8c`, the skill's suite runs 747 tests with one skip and passes, the shared suite runs 208 and passes, and the shared check reports 0 findings over the skill's 50 files. The extraction is checked against the commit it is cut from.
- **Ground that moves.** workflow-server's `workspace` keeps moving until the extraction; the extracted commit, not `785a5ee8c`, is the comparison point.
