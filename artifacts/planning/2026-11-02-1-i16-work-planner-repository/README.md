# Work Planner Repository — November 2026

> Planning record · Created 2026-11-02

## Executive Summary

This record plans I16, which gives the work-planner skill a repository of its own. The skill, with its history and the shared guidelines, rules and check it is held to, moves from workflow-server's `skills/` folder to the root of prosiform-skills. workflow-server's `workspace` template then takes the skill from a pinned submodule in place of its plain copy, and the board's Priority field becomes the one source of an epic's rank.

It matters because the skill's history, pull requests and planning have shared a repository with unrelated work, and every workspace made from the template receives a plain copy with no version recorded. One home makes the skill's own changes reviewable on their own, and a pinned submodule makes the installed version a deliberate choice.

## Artifacts

| Artifact | What it holds |
| --- | --- |
| [Decisions](decisions.md) | The user's decisions, the planning decisions taken from them, the open question with its recommendation, and the proposed order |
| [Goal trace](goal-trace.md) | Each goal clause traced to its criteria and epics, the ranked gaps and the outside threats |
| [Pair decisions](joins.md) | The rows kept separate and the rows joined into one pull request, and why |
| [E00 W00](e00/w00.md) | Skill history extracted into `main` |
| [E00 W01](e00/w01.md) | Long-lived branches stated |
| [E00 W02](e00/w02.md) | Scripts named relative to the skill |
| [E00 W03](e00/w03.md) | Shared check run from the root |
| [E01 W01](e01/w01.md) | Deploy checks out submodules |
| [E01 W02](e01/w02.md) | Update checks out submodules |
| [E01 W03](e01/w03.md) | Work planner from a pinned submodule |
| [E01 W04](e01/w04.md) | Plain copy removed from the template |
| [E02 W01](e02/w01.md) | Priority Number field on every board |
| [E02 W02](e02/w02.md) | Board Queue reads the Priority field |
| [E02 W03](e02/w03.md) | Planning sets the Priority field |
| [E02 W04](e02/w04.md) | Template pins a skill reading the field |
| [E02 W05](e02/w05.md) | Priority labels deleted, delivered by the listing it records |

## Links

| Resource | Link |
| --- | --- |
| Initiative | [I16](https://github.com/m2ux/prosiform-skills/issues/1) |
| Skill Migration | [I16:E00](https://github.com/m2ux/prosiform-skills/issues/2) |
| Submodule Install | [I16:E01](https://github.com/m2ux/prosiform-skills/issues/3) |
| Priority Field | [I16:E02](https://github.com/m2ux/prosiform-skills/issues/4) |
| Carried-over issue | [m2ux/workflow-server#1595](https://github.com/m2ux/workflow-server/issues/1595) |
| Board | [Process: How Work Is Planned and Delivered](https://github.com/users/m2ux/projects/17) |
