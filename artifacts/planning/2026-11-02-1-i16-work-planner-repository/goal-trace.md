# I16 Goal Trace

The goal clauses are the user's decisions of 2 November 2026, recorded in [decisions](decisions.md). Each source requirement below is one of those decisions, or m2ux/workflow-server#1595, which decision 9 carries over whole. Clauses G1 to G4 are decision 12.

## Trace Table

| Goal clause | Initiative criteria | Epics | Epic criteria | Source requirement |
| --- | --- | --- | --- | --- |
| The skill and its shared files move unchanged to prosiform-skills' root with their history | AC1 | E00 | E00 AC1, AC2, AC3, AC4 | Decisions 1, 2, 4, 6 |
| prosiform's workspace runs the skill from a pinned prosiform-skills commit, through a link | AC4 | E01 | E01 AC1, AC2, AC3, AC4, AC5 | Decisions 5, 6 |
| workflow-server's template carries no copy, and its skill files outside workflow-canon name none | AC3 | E01 | E01 AC6, AC7, AC8 | Decisions 3, 5, 8 |
| The skill's tests and the shared check pass from the new root | AC2 | E02 | E02 AC1, AC2, AC3, AC4 | Decisions 1, 6, 7 |
| Board Queue ranks by the board's Priority Number field alone | AC5 | E03 | E03 AC1, AC2, AC3, AC4, AC5, AC6 | Decision 9; #1595 AC1–AC4 |
| No `priority:` label remains | AC6 | E03 | E03 AC7 | Decisions 9, 10; #1595 AC5 |
| G1: every mode compiles within the default budget with no warning | AC7 | E07 | E07 AC2, AC6, AC8 | Decision 12, G1 |
| G2: SKILL.md bootstraps by running `pf` | AC8 | E07 | E07 AC1 | Decision 12, G2 |
| G2: a link stands only where its content is needed, names its section, and a mention is plain text | AC9 | E06, E07 | E06 AC1, AC2; E07 AC4, AC5, AC8 | Decision 12, G2 |
| G2: hand-offs dispatch and conditional reads defer | AC10 | E06 | E06 AC3, AC4 | Decision 12, G2 |
| G1, G2: no mode's bundle grows against the baseline | AC11 | E07 | E07 AC3 | Decision 12, G1; decision 17 |
| G3: the shared guide states the prosiform rules | AC12 | E04 | E04 AC1, AC2, AC3, AC4, AC5 | Decision 12, G3 |
| G3: the shared check enforces them over every skill it runs over | AC13 | E07 | E07 AC4, AC5, AC6, AC7 | Decision 12, G3; decision 15 |
| G4: each check is defined where prose names it | AC14 | E05 | E05 AC1, AC2, AC3, AC4 | Decision 12, G4 |

Every epic criterion is delivered by a task row, as each epic's Coverage column shows and `format.py` reports.

## Gaps

Ranked, the first most threatening the goal.

1. **prosiform between link and removal.** prosiform's link must merge before the template's removal, or its next template update leaves it with no skill. The removal row depends on the link row; prosiform's own update timing is its owner's.
2. **Checkouts before the scripts reach them.** A prosiform checkout that pulls the link without the template's submodule checkout has an empty submodule. The link's pull request merges the template's script change first.
3. **Other forks of the template.** A workspace other than prosiform's loses work-planner at its next template update. The initiative's Non-Goals state that the template ships no work-planner.
4. **Labels before the field is read.** The label deletion depends on prosiform pinning a skill that reads the field.
5. **workflow-canon's stale command.** `skills/workflow-canon/references/revise-mode.md` still runs the check and a test suite over `skills/work-planner`, which the template no longer holds. The initiative's Non-Goals keep it.
6. **The prosiform version is open.** The installed `pf` is `skill-markdown-v1` while prosiform's `main` is `skill-markdown-v4`, whose guide the bootstrap needs. E04 and E07 carry OQ1; one version compiles both sides of the comparison.
7. **The baseline is open.** E07's comparison has no fixed baseline until OQ2 is settled; it is settled before E07 starts, and the baseline is a revision the plan does not change.
8. **The check needs `pf` wherever it runs.** Once E07's compile run lands, a host without the pinned `pf` gets a finding rather than a clean report, by design: an absent instrument never passes silently.
9. **Record of where skill changes go.** md-composer's agent memory states that skill changes go to workflow-server's `workspace`. After the cutover, work-planner changes go to prosiform-skills' `main`.

## Outside Threats

- **Readers of what moves.** `deploy-workspace.sh` and `update-workspace.sh` read a workspace's tree, and each gains a submodule checkout before any workspace declares one. No hook or settings file in md-composer names the skill's path.
- **Fail-closed paths.** A missing `config/branches` leaves branch names unevaluable rather than guessed; until the branch list merges, base preparation takes the names from decision 4.
- **Baseline.** At workflow-server `785a5ee8c`, the skill's suite runs 747 tests with one skip and passes, the shared suite runs 208 and passes, and the shared check reports 0 findings over the skill's 50 files. The extraction is checked against the commit it is cut from.
- **Ground that moves.** workflow-server's `workspace` keeps moving until the extraction; the extracted commit, not `785a5ee8c`, is the comparison point.
- **A check run that hides a violation.** A compile skipped when `pf` is absent would report a clean skill; E07 AC7 makes an absent or mismatched `pf` a finding.
- **Findings before conformance.** Each prosiform finding lands only after the files it reads conform: E05's bare-path finding after its prose links, E07's findings after E06 and E07's own conformance rows, so no epic base carries a finding against its own files.
- **workflow-server's copy of the check.** workflow-canon runs workflow-server's diverging copy, which this initiative does not change, so the new findings reach no skill outside prosiform-skills.
- **Instrument independent of the measured.** E06 is verified by recorded inventories rather than by the check E07 extends; E07's bundle comparison compiles both revisions with one `pf`.
