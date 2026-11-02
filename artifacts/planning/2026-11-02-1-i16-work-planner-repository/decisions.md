# I16 Decisions

## The User's Decisions, 2 November 2026

1. **Layout.** The repository root holds `work-planner/`, with the shared `guidelines.md`, `rules.json`, `scripts/` (`check_skill_files.py` and anything it imports) and `test/` beside it: workflow-server's `skills/` folder moved up one level. Only work-planner moves; gitnexus, workflow-canon and server-in-the-loop stay in workflow-server.
2. **History.** Kept. The history of `skills/work-planner` and the shared files is extracted with `git filter-repo`, paths moved up one level, and the result's tree is checked against `workspace`'s head.
3. **Old home.** Once prosiform-skills holds the skill, the plain copy of `skills/work-planner` is deleted from workflow-server's `workspace`. Each repository owns its own copy of the shared files, and the copies may diverge. workflow-server's shared check and tests lose every reference to work-planner.
4. **Branches.** Task and epic pull requests target `main`. Planning records live on an orphan `engineering` branch, and `config/branches` names both.
5. **Install.** workflow-server's `workspace` template takes the skill from a prosiform-skills submodule pinned to a commit on `main`. Every workspace made or updated from the template, md-composer among them, receives the pin through the template's deploy and update scripts, and needs no task of its own.
6. **Priority field.** m2ux/workflow-server#1595 becomes an epic whole. Priority is a Number field on every theme board and the Initiative template, a larger number runs first, and an empty value never starts. Numbered labels move into the field unchanged, word labels move nothing, and every `priority:` label is then deleted. Board Queue reads only the field. #1595 is closed as not planned, linking the epic.

## The User's Decisions on the Open Points, 2 November 2026

1. **Script naming.** A command names its script relative to `SKILL.md`, as `scripts/<name>.py`, and every procedure runs from the skill's folder. There is no placeholder for the skill's folder; `<workspace>` still supplies `scripts/sbx`.
2. **workflow-canon stays untouched.** The removal edits nothing under `skills/workflow-canon`, and its `references/revise-mode.md` still names `skills/work-planner`, as the initiative's Non-Goals state.
3. **Submodule layout.** The submodule sits at `vendor/prosiform-skills`, a full checkout with no sparse checkout, and `skills/work-planner` is a tracked symlink to `../vendor/prosiform-skills/work-planner`.
4. **Label deletion is its own row.** It takes no pull request and is delivered by the before-and-after label listing committed to this record, as the history extraction is delivered by its commit. Every pull-request task's criteria are ticked at merge.
5. **The removal belongs to the install.** The plain copy's removal is the install epic's row, joined with the submodule row so both land in one pull request and no fork of the template has neither copy. The migration epic only builds the new home.
6. **No priority set.** Only the user ranks work; this record carries the proposed order alone.

## Planning Decisions

- **Labels exist before the plan.** The labels the issue templates require are created in prosiform-skills during planning, because the initiative and its epics carry them at creation: `bot:ai-assisted`, `type:initiative`, `type:epic`, `type:task`, `type:proposal`, `theme:planning` and `tech-debt`, with workflow-server's colours and descriptions. No task carries them.
- **`main` restored as default.** Pushing the orphan `engineering` branch to the empty repository made it the default branch. The task that first publishes `main` sets it back.
- **The extraction is preparatory work.** No epic base can be cut before `main` exists, so the extraction is pushed directly and delivered by its commit.
- **The branch list is a pull request.** `config/branches` lands through the epic base like any task; until it merges, base preparation takes the names from decision 4.
- **The scripts learn submodules first.** `deploy-workspace.sh` and `update-workspace.sh` check out submodules before the template carries one, so no workspace is ever made with a dangling link. They need nothing from the new repository and can start at once.
- **The pin follows the migration.** The submodule pins `main` after the migration's base merges, which carries every migration row on `main`.
- **No skill change beyond the migration while two copies exist.** The Priority Field epic's first row waits for the joined submodule and removal rows, so no change is made to one copy and not the other. That makes both earlier epics whole-epic prerequisites of the Priority Field epic.
- **Labels go last.** Deleting the labels while an installed copy still reads them would leave that copy's queue with no priority, so they go only after the template pins a skill that reads the field.
- **Joined queue change.** Board Queue's read and every other priority mention change in one pull request, so the skill never reads one source and names another.

## Proposed Order

`deps.py` proposes E00 and E01 at 2 and E02 at 1. The migration and the template's script changes start together; the joined submodule and removal rows wait for the migration's `main` rows; the Priority Field epic follows them. No contending pair separates any two epics.
