# I16 Decisions

## The User's Decisions, 2 November 2026

1. **Layout.** The repository root holds `work-planner/`, with the shared `guidelines.md`, `rules.json`, `scripts/` (`check_skill_files.py` and anything it imports) and `test/` beside it: workflow-server's `skills/` folder moved up one level. Only work-planner moves; gitnexus, workflow-canon and server-in-the-loop stay in workflow-server.
2. **History.** Kept. The history of `skills/work-planner` and the shared files is extracted with `git filter-repo`, paths moved up one level, and the result's tree is checked against `workspace`'s head.
3. **Old home.** Once the skill is linked where it is used, workflow-server's `workspace` template drops its copy of `skills/work-planner`. Each repository owns its own copy of the shared files, and the copies may diverge. workflow-server's shared check and tests lose every reference to work-planner.
4. **Branches.** Task and epic pull requests target `main`. Planning records live on an orphan `engineering` branch, and `config/branches` names both.
5. **Skills belong to each workspace.** workflow-server's template adds no prosiform-skills submodule. It supports the vendor pattern: its deploy and update scripts check out whatever submodules a workspace declares. The workspace that uses the skill, prosiform's (`m2ux/prosiform`, branch `workspace`), adds `vendor/prosiform-skills` as a full submodule with no sparse checkout, pinned to a prosiform-skills `main` commit, and makes `skills/work-planner` a tracked symlink to `../vendor/prosiform-skills/work-planner`.
6. **Cutover before refactoring.** The skill moves as it is, with no change to its content, and works in prosiform's workspace through the symlink unchanged. Script naming relative to the skill, the shared check run from the root, and the Priority field come afterwards.
7. **Script naming.** A command names its script relative to `SKILL.md`, as `scripts/<name>.py`, and every procedure runs from the skill's folder. There is no placeholder for the skill's folder; `<workspace>` still supplies `scripts/sbx`.
8. **workflow-canon stays untouched.** The removal edits nothing under `skills/workflow-canon`, and its `references/revise-mode.md` still names `skills/work-planner`, as the initiative's Non-Goals state.
9. **Priority field.** m2ux/workflow-server#1595 becomes an epic whole. Priority is a Number field on every theme board and the Initiative template, a larger number runs first, and an empty value never starts. Numbered labels move into the field unchanged, word labels move nothing, and every `priority:` label is then deleted once prosiform's workspace pins the field-reading skill. Board Queue reads only the field. #1595 is closed as not planned, linking the epic.
10. **Label deletion is its own row.** It takes no pull request and is delivered by the before-and-after label listing committed to this record, as the history extraction is delivered by its commit. Every pull-request task's criteria are ticked at merge.
11. **Ranking.** Only the user ranks work. The user ranks E00 and E01 at 5, E02 and E03 at 4, E04 at 3, E05 and E06 at 2, and E07 at 1, applied as `priority: <n>` labels while I16 still ranks by labels. The initiative keeps `priority: 2`.
12. **Used through prosiform.** I16's goal also holds four clauses, confirmed for the prosiform epics:
    - **G1.** Every Work Planner mode compiles under prosiform (`pf`) within its default output budget with no warnings.
    - **G2.** Work Planner is used through `pf`: SKILL.md bootstraps by running `pf` and following it; sub-agent hand-offs use the dispatch operators (`⇉`, `⫽`) and material read only in some cases uses deferral (`¬`); a link appears only where the reader must have its content, and prose that merely names another mode uses plain text; links name a section wherever the target has a heading.
    - **G3.** The shared skill guidelines (`guidelines.md`) and the shared check (`scripts/check_skill_files.py`, with its tests) state and enforce those prosiform rules.
    - **G4.** The shared guide defines each check the repository runs (what it decides, which skills it binds, how it is run, where its tests live), and prose names a check by linking to that definition rather than by bare path.
13. **Four epics after the Priority field.** E04 Shared Prosiform Rules, E05 Check Definitions, E06 Work Planner Links and E07 Use Through Prosiform, in that order. No proposal stands behind them; the clauses above are their source.
14. **Paths at the new root.** Every file-change declaration, component and criterion instrument names prosiform-skills' root layout (`guidelines.md`, `scripts/check_skill_files.py`, `test/`, `work-planner/`), commands name scripts relative to the skill as decision 7 states, and pull requests target `main`.
15. **Every skill the check reads is held.** The shared check holds every skill it runs over to the prosiform rules; no option names the skills it holds. workflow-server keeps its own diverging copy of the check, as decision 3 states. The check gains its prosiform findings last in E07, after Work Planner's files conform, so no branch carries a finding against its own files.
16. **Dependencies follow the link.** E04 to E07 depend on E02's rows where they share files (SKILL.md, command paths, `scripts/check_skill_files.py`, the guide's examples) and follow E03's rows where they share files (`plan-mode.md`, Board Queue).
17. **Baseline revision.** Held open, and settled before E07 starts. See [OQ2](#oq2-baseline-revision).
18. **Prosiform version.** Held open while prosiform is under heavy revision, and settled before E04 and E07 start. Bodies name the pinned `pf` without a version. See [OQ1](#oq1-grammar-version).
19. **#1427 in References.** m2ux/workflow-server#1427 is cited in I16's References as the source of the carried evidence. It stands on board 17, which the same-board References rule bars; the user keeps it as a recorded departure.
20. **#1427 closes as not planned.** Its section-scoped links, plain-text mentions and conditional citations are carried into E06, and its check definitions into E05. Its remaining rows and efficacy walks need no work, because prosiform bundles linked content at compile time.
21. **One home for the record.** The prosiform plan drafted in workflow-server's `engineering` branch is merged into this record, and the draft folder is deleted there.
22. **No Deferred Debt epic.** Findings are fixed in the delivery that finds them.
23. **Fixes land before the extraction.** E00 W00 depends on [m2ux/workflow-server I17:E00](https://github.com/m2ux/workflow-server/issues/1598), Pre-Cutover Fixes, which delivers every Work Planner fix found before the cutover into workflow-server's `workspace`. The extraction is cut from a `workspace` commit holding all of them, so it carries each fix. The cell names the epic, not its rows, because that epic takes further rows as faults are found.
24. **Extraction point.** E00 W00 cuts the extraction from workflow-server's `workspace` head once I17's Pre-Cutover Fixes epic closes, and records that commit in this record. No plan names the commit in advance; `785a5ee8c` is the evidence revision only.

## Planning Decisions

- **Labels exist before the plan.** The labels the issue templates require are created in prosiform-skills during planning, because the initiative and its epics carry them at creation: `bot:ai-assisted`, `type:initiative`, `type:epic`, `type:task`, `type:proposal`, `theme:planning` and `tech-debt`, with workflow-server's colours and descriptions. No task carries them.
- **`main` restored as default.** Pushing the orphan `engineering` branch to the empty repository made it the default branch. The task that first publishes `main` sets it back.
- **The extraction is preparatory work.** No epic base can be cut before `main` exists, so the extraction is pushed directly and delivered by its commit.
- **The branch list is a pull request.** `config/branches` lands through the epic base like any task; until it merges, base preparation takes the names from decision 4.
- **Cross-repository order.** The template's deploy and update scripts learn submodules first, in workflow-server. prosiform's link merges the template's `workspace` first, carrying that change, then adds the submodule and the symlink, pinned to the extraction's `main` commit. Only then does the template drop its copy.
- **How the removal reaches prosiform.** prosiform takes the template's deletion at its next `update-workspace.sh`. Both sides have deleted the plain files, and only prosiform's side holds the symlink at `skills/work-planner`, so the merge keeps the symlink with no conflict. The removal's review runs that merge on a scratch copy before it merges.
- **Refactoring waits for the link.** The refactor and Priority Field epics start only after the template's copy is gone, so no change is made to one copy and not the other. Their first rows name the branch list and the removal, which makes both the cutover and the linkage whole-epic prerequisites.
- **One contending pair, answered by order.** The extraction and the refactor's script-naming row both declare `main:work-planner/SKILL.md`. The extraction lands before the refactor can start, and the proposed numbers separate the two epics.
- **Labels go last.** Deleting the labels while an installed copy still reads them would leave that copy's queue with no priority, so they go only after prosiform's workspace pins a skill that reads the field.
- **Joined queue change.** Board Queue's read and every other priority mention change in one pull request, so the skill never reads one source and names another.
- **Rules before conformance.** E04 states the prosiform rules in `guidelines.md` only; the check machinery that enforces them is E07's last two rows, joined in one pull request.
- **Prose before its finding.** E05 links each check's definition from prose before the check reports a bare check path, so E05's base never carries that finding.
- **Inventories verify E06.** The check's prosiform findings land after E06, so E06's criteria are verified by the link, mode-link, hand-off and conditional-citation inventories each task records here, an instrument independent of the check. E07's final run of the check confirms them on `main`.
- **The bundle comparison is a record.** E07 W04 takes no pull request and is delivered by the comparison committed to this record, as the label deletion is delivered by its listing.
- **The Checks entry grows with the check.** E05 defines each check as it stands; E07's check rows extend the shared check's entry with the findings and compile run they add.
- **Measurements carried from the draft.** The bundle sizes, link counts and check callers were measured at workflow-server `785a5ee8c`, the evidence revision, with `pf` 0.12.0. See [Evidence](evidence.md).

## Proposed Order

[`deps.py`](dependencies.txt) proposes E00 and E01 at 4, E02, E03 and E04 at 3, E05 and E06 at 2, and E07 at 1. The user's ranking, decision 11, keeps that order and separates E04 from E02 and E03, so every contending pair the report prints sits in epics of different numbers. Within the linkage, the template's script rows can start at once; prosiform's link waits for them and for the extraction, and the template's removal waits for the link.

## Open Questions

### OQ1. Grammar Version

The installed `pf` reports 0.12.0 (`skill-markdown-v1`). Prosiform's README and source on `main` name `skill-markdown-v4` at 0.16.0, unreleased; the latest release, 0.15.0, is `skill-markdown-v3`. The bootstrap the goal names, run bare `pf` and follow the guide it prints, exists only on `main`.

The user holds the version undecided while prosiform is under heavy revision. Bodies name the pinned `pf` without a version. Settled before E04 or E07 starts.

The pin is v0.24.0 or later (user, 9 November 2026): on `pf` 0.23.0, SKILL.md and eight of ten modes fail an internal no-accidental-expansion check that [prosiform#703](https://github.com/m2ux/prosiform/issues/703) (F09) fixes, released as `contract/v0.24.0` and `python/v0.24.0` on 9 November 2026. No epic waits on a hot-fix, so this open question is what holds E04 and E07.

### OQ2. Baseline Revision

The baseline E07's bundle-size comparison measures against. Settled before E07 starts.

- **A.** The extraction commit on prosiform-skills' `main`, cut from workflow-server's `workspace` head once I17's Pre-Cutover Fixes epic closes.
- **B.** workflow-server `ed508443`, whose Work Planner markdown equals md-composer `93dad5b9`; md-composer `93dad5b9` is not a workflow-server object.

## Joined Check Definitions, 5 November 2026

The user confirms E05 W01 and W02 as one pull request, waiting for both E02 W01 and W02. The Joins cells are reciprocal; there is no dependency between members. Their prerequisite union derives E02 as E05's initiative-level prerequisite. The unit is unlaned, and the third row consumes its completed prose output through W02. The row ids, criteria and work items retain their identities.

## Prosiform Adoption, 9 November 2026

A trial on a copy of the skill, `prosiform: {}` on each of its 59 documents under `pf` 0.23.0, compiled propose (55711-byte bundle) and revise (65375); every other entry failed the check OQ1 records.

- **Modes are the entries.** SKILL.md is read, not compiled: its Modes list selects a mode, and its instruction is to run `pf` on that mode file. E07 W01, its AC1 and the initiative's AC8 state the routing (user).
- **Sub-agent steps split first.** A mode over the budget hands each step a sub-agent runs to a `⇉` link with a bundle of its own before any section moves; a budget is raised only for a mode still over after both (user).
- **Each mode compiles against stubs.** A `test` preset per mode replaces its artifacts and protocols with stubs through `subst`, and the skill's test suite compiles every mode with it. E07 W07 carries it, depending on W03, covering E07 AC9 and the initiative's AC15 (user).
- **No new initiative.** The adoption is folded into this one rather than raised in workflow-server (user).

## Content Grain, 9 November 2026

- **A grain review precedes the budget fit.** E07 W02 measures each protocol and artifact, and each procedure, operation, command and field section it holds, for bundle share, reach, dead weight and cohesion, and gives each a verdict of keep, split, merge or move (user).
- **Analysis, then planned changes.** The report lives in this record; each confirmed split, merge or move becomes an E07 row ahead of W03, the budget fit (user).
- **After the links, before the fit.** E07 W02 depends on E06:W03, so it measures links as E06 leaves them, and W03 depends on W02. The grain review takes W02 and the rows after it move up one, so each task depends only on earlier ones (user).
- **A rubric for Work Planner.** The measures, thresholds and verdict rules are stated in `work-planner/references/grain-rubric.md`, and Revise Mode holds each new or changed protocol and artifact to it. The rubric is Work Planner's own, since its structure is not necessarily shared by other skills; the shared guidelines gain no grain rule (user).
