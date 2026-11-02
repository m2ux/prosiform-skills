# I16 Prosiform Epics Review

Plan Mode's Review Initiative Goal over the prosiform epics, E04 to E07, and the initiative that carries them. Format results: `format.py` over each body. Ordering: the [dependency report](dependencies.txt). Epic numbers below are I16's.

## Round 1, Drafted as a Separate Initiative

### Criteria

- **R1-1. Initiative criteria restated single epic criteria.**  Major.
  - Problem: the draft's initiative criteria each restated one epic criterion. Source: initiative-issue-body.md Initiative Acceptance Criteria, "One that restates a single epic's criterion is a duplicate".
  - Resolution: raised to what the epics achieve together; link scope, operators and check definitions each one outcome. Applied.
- **R1-2. A criterion joined two invariants.**  Minor.
  - Problem: `format.py`: "AC3 may state several invariants; state one per criterion".
  - Resolution: restated as one condition, no link compiling content its reader need not have (I16 AC9). Applied.
- **R1-3. The budget criterion restates E07 AC2.**  Minor.
  - Problem: the same duplicate rule.
  - Resolution: kept; I16 AC7 is goal clause G1 and E07 AC2 is the row that makes it true. Recorded.

### Format

- **R1-4. Change narrative in References.**  Minor.
  - Problem: `format.py` flagged the word superseded in the #1427 reference.
  - Resolution: the reference states what #1427 holds. Applied.
- **R1-5. E05 title over length.**  Minor.
  - Problem: `format.py`: "title subtitle runs to 11 words"; Issue Body Titles, "The name is two or three words".
  - Resolution: `[I16:E05] Check Definitions: Each Check Defined in the Shared Guide, Named by Link`. Applied.

### Ordering

- **R1-6. Implied and missing epic edges.**  Minor.
  - Problem: `deps.py` reported an implied edge and two missing initiative edges.
  - Resolution: dropped the implied edge and set both initiative cells. Applied.

### Outside Threats

- **R1-7. An absent instrument could pass silently.**  Major.
  - Problem: a check that skips the compile when `pf` is missing would report a clean skill.
  - Resolution: E07 AC7 makes an absent or mismatched `pf` a finding.
- **R1-8. The instrument's version moves the measurements.**  Major.
  - Problem: installed `pf` is `skill-markdown-v1`; prosiform `main` is `skill-markdown-v4`, whose guide the bootstrap needs. See [evidence](evidence.md#instrument).
  - Resolution: E07 AC3 compares both revisions with one version; which version is [OQ1](decisions.md#oq1-grammar-version).
- **R1-9. The stated baseline does not resolve in workflow-server.**  Major.
  - Problem: `93dad5b9` is an md-composer commit; `git cat-file` in workflow-server: "Not a valid object name 93dad5b9".
  - Resolution: [OQ2](decisions.md#oq2-baseline-revision), held open by the user.

### Skill

- **R1-10. Same-board reference.**  Advisory.
  - Problem: issue-body.md References, "An issue's References section does not link issues or pull requests on the same board"; #1427 stands on board 17.
  - Resolution: kept as a recorded departure, decision 19.

## Round 2, Integrated into I16

### Structure

- **R2-1. A check caller outside the repository.**  Major.
  - Problem: the draft held the prosiform findings to skills named by a command-line option, so workflow-canon's run of the check drew none.
  - Resolution: decision 15. The check holds every skill it runs over; workflow-canon runs workflow-server's own copy. The option and its criterion are gone. Applied.
- **R2-2. Findings against a branch's own files.**  Major.
  - Problem: with no naming option, check findings landing in E04 would report against Work Planner on every base until E06 and E07 conform.
  - Resolution: the link-scope, mode-reach and compile findings are E07 W04 and W05, joined, after E07 W01 and W02; E04 states the rules only. Applied.
- **R2-3. A finding before the prose it reads.**  Minor.
  - Problem: E05's bare-path finding preceded the row that links each check from prose, so E05's base would carry it between merges.
  - Resolution: E05 W02 links the prose and W03 adds the finding. Applied.
- **R2-4. E06's instrument does not exist yet.**  Major.
  - Problem: E06 AC1 and AC2 were observed by check findings that now land in E07.
  - Resolution: E06 AC1 and AC2 are observed by the link and mode-link inventories each task records here; E07 AC8 confirms them through the check. Applied.
- **R2-5. The compile run had no Checks entry.**  Minor.
  - Problem: E05 defined the compile run, which lands in E07.
  - Resolution: E07 W04 and W05 extend the shared check's Checks entry, and `guidelines.md` enters their declarations. Applied.

### Paths and Format

- **R2-6. Paths named the old layout.**  Major.
  - Problem: every declaration and instrument named `skills/…`.
  - Resolution: decision 14; root paths, and commands in the form E02 establishes. Applied.
- **R2-7. A count in an initiative criterion.**  Minor.
  - Problem: `format.py`: "AC13 carries a count (3)", from a command naming `python3`.
  - Resolution: AC13 names the check's own test suite. Applied; `format.py` reports nothing on any of the nine bodies.

### Ordering

- **R2-8. E06's initiative edge.**  Minor.
  - Problem: `deps.py`: "initiative E06: Depends on should be E02, E04, not E00, E01".
  - Resolution: set. Applied.
- **R2-9. Independent pairs unaccounted.**  Minor.
  - Problem: `deps.py` listed E01 W01 and W02, E02 W01 and W02, E07 W01 and W02, and E07 W03 with W04 and with W05.
  - Resolution: each recorded with why in [joins](joins.md). Applied.
- **R2-10. Component contention.**  Advisory.
  - Problem: `guidelines.md` (E04, E05), `scripts/check_skill_files.py` (E02, E05, E07), `work-planner/SKILL.md` (E00, E02, E06, E07) and `deliver-mode.md` (E06, E07) are each extended from two or more epics.
  - Resolution: the user's ranking, decision 11, puts every contending pair in epics of different numbers.

## Round 3

Review Initiative Goal repeated over the saved bodies: every clause traces to a criterion and every criterion to an epic and a task row ([trace](goal-trace.md)); `format.py` reports nothing to fix, apply or decide on the initiative or any of its eight epics; `deps.py` reports no problem. No content or structural finding remains. OQ1 stands on E04 and E07, OQ2 on E07.
