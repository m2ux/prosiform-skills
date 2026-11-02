# I16 Decisions

## The User's Decisions, 2 November 2026

1. **Layout.** The repository root holds `work-planner/`, with the shared `guidelines.md`, `rules.json`, `scripts/` (`check_skill_files.py` and anything it imports) and `test/` beside it: workflow-server's `skills/` folder moved up one level. Only work-planner moves; gitnexus, workflow-canon and server-in-the-loop stay in workflow-server.
2. **History.** Kept. The history of `skills/work-planner` and the shared files is extracted with `git filter-repo`, paths moved up one level, and the result's tree is checked against `workspace`'s head.
3. **Old home.** Once prosiform-skills holds the skill, `skills/work-planner` is deleted from workflow-server's `workspace`. Each repository owns its own copy of the shared files, and the copies may diverge. workflow-server's shared check and tests lose every reference to work-planner.
4. **Branches.** Task and epic pull requests target `main`. Planning records live on an orphan `engineering` branch, and `config/branches` names both.
5. **Local install.** md-composer takes `.claude/skills/work-planner` from a git submodule of prosiform-skills, pinned to a commit.
6. **Priority field.** m2ux/workflow-server#1595 becomes an epic whole. Priority is a Number field on every theme board and the Initiative template, a larger number runs first, and an empty value never starts. Numbered labels move into the field unchanged, word labels move nothing, and every `priority:` label is then deleted. Board Queue reads only the field. #1595 is closed as not planned, linking the epic.

## Planning Decisions

- **Labels exist before the plan.** The labels the issue templates require are created in prosiform-skills during planning, because the initiative and its epics carry them at creation: `bot:ai-assisted`, `type:initiative`, `type:epic`, `type:task`, `type:proposal`, `theme:planning` and `tech-debt`, with workflow-server's colours and descriptions. No task carries them.
- **`main` restored as default.** Pushing the orphan `engineering` branch to the empty repository made it the default branch. The task that first publishes `main` sets it back.
- **The extraction is preparatory work.** No epic base can be cut before `main` exists, so the extraction is pushed directly and delivered by its commit.
- **The branch list is a pull request.** `config/branches` lands through the epic base like any task; until it merges, base preparation takes the names from decision 4.
- **No skill change beyond the migration while two copies exist.** The Priority Field epic starts only after workflow-server's copy is deleted, so no change is made to one copy and not the other. That makes the migration a whole-epic prerequisite of both later epics.
- **The pin follows the migration.** The submodule pins `main` after the migration's base merges, which carries every migration row on `main`, and its pull request takes workflow-server's deletion in the same merge.
- **Labels go last.** Deleting the labels while an installed copy still reads them would leave that copy's queue with no priority, so they go only after md-composer's pin moves to a skill that reads the field.
- **Joined queue change.** Board Queue's read and every other priority mention change in one pull request, so the skill never reads one source and names another.
- **No priority set.** Only the user ranks work; the record carries the proposed order alone.

## Open Question

- **How a command names its script.** The skill's commands name `skills/work-planner/scripts/<name>.py` from the host checkout, which holds only under a `skills/` folder.
  - **Recommended.** A `<skill>` placeholder for the folder holding `SKILL.md`, so each command names `<skill>/scripts/<name>.py`, and `<workspace>` stays the checkout an agent works in, which supplies `scripts/sbx`. The command then holds in prosiform-skills and in any workspace that installs the skill.
  - **Alternative.** Commands keep a host-relative path and each install mounts the skill under `skills/work-planner`. prosiform-skills' own tests then read a path its own checkout does not have.

## Proposed Order

`deps.py` proposes E00 at 2 and E01 and E02 at 1: the migration first, then the install and the Priority field together. No contending pair separates E01 from E02. Within E02, the field rows can run while E01 is under way; only the final row waits for E01's submodule.
