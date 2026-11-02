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
11. **Ranking.** Only the user ranks work. The user set `priority: 2` on I16, E00 and E01, and `priority: 1` on E03 (issue #4); the Skill Refactor epic (#5) carries none until the user re-ranks.

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

## Proposed Order

`deps.py` proposes E00 and E01 at 2, and E02 and E03 at 1: the cutover and the workspace linkage first, together, then the refactor and the Priority field, together. Within the linkage, the template's script rows can start at once; prosiform's link waits for them and for the extraction, and the template's removal waits for the link.
