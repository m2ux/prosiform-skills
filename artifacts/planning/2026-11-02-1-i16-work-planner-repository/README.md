# Work Planner Repository — November 2026

> Planning record · Created 2026-11-02

## Executive Summary

This record plans I16, which gives the work-planner skill a repository of its own. The skill, with its history and the shared guidelines, rules and check it is held to, moves unchanged from workflow-server's `skills/` folder to the root of prosiform-skills. prosiform's workspace then runs it from a pinned submodule through a link, workflow-server's template drops its copy, and only after that is the skill refactored for its new root and the board's Priority field made the one source of an epic's rank.

It matters because the skill's history, pull requests and planning have shared a repository with unrelated work, and the workspace that uses it receives a plain copy with no version recorded. One home makes the skill's own changes reviewable on their own, and a pinned submodule makes the installed version a deliberate choice of the workspace that uses it.

## Artifacts

| Artifact | What it holds |
| --- | --- |
| [Decisions](decisions.md) | The user's decisions, the planning decisions taken from them, and the proposed order |
| [Goal trace](goal-trace.md) | Each goal clause traced to its criteria and epics, the ranked gaps and the outside threats |
| [Pair decisions](joins.md) | The rows kept as separate pieces of work, and why |
| [E00 W00](e00/w00.md) | Skill history extracted into `main`, unchanged |
| [E00 W01](e00/w01.md) | Long-lived branches stated |
| [E01 W01](e01/w01.md) | Deploy checks out submodules |
| [E01 W02](e01/w02.md) | Update checks out submodules |
| [E01 W03](e01/w03.md) | prosiform workspace links the skill |
| [E01 W04](e01/w04.md) | Plain copy removed from the template |
| [E02 W01](e02/w01.md) | Scripts named relative to the skill |
| [E02 W02](e02/w02.md) | Shared check run from the root |
| [E03 W01](e03/w01.md) | Priority Number field on every board |
| [E03 W02](e03/w02.md) | Board Queue reads the Priority field |
| [E03 W03](e03/w03.md) | Planning sets the Priority field |
| [E03 W04](e03/w04.md) | prosiform pins a skill reading the field |
| [E03 W05](e03/w05.md) | Priority labels deleted, delivered by the listing it records |

## Links

| Resource | Link |
| --- | --- |
| Initiative | [I16](https://github.com/m2ux/prosiform-skills/issues/1) |
| Skill Cutover | [I16:E00](https://github.com/m2ux/prosiform-skills/issues/2) |
| Workspace Linkage | [I16:E01](https://github.com/m2ux/prosiform-skills/issues/3) |
| Skill Refactor | [I16:E02](https://github.com/m2ux/prosiform-skills/issues/5) |
| Priority Field | [I16:E03](https://github.com/m2ux/prosiform-skills/issues/4) |
| Carried-over issue | [m2ux/workflow-server#1595](https://github.com/m2ux/workflow-server/issues/1595) |
| Board | [Process: How Work Is Planned and Delivered](https://github.com/users/m2ux/projects/17) |
