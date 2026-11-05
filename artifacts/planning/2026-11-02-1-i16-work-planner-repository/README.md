# Work Planner Repository — November 2026

> Planning record · Created 2026-11-02

## Executive Summary

This record plans I16, which gives the work-planner skill a repository of its own. The skill, with its history and the shared guidelines, rules and check it is held to, moves unchanged from workflow-server's `skills/` folder to the root of prosiform-skills. prosiform's workspace then runs it from a pinned submodule through a link, workflow-server's template drops its copy, and only after that is the skill refactored for its new root and the board's Priority field made the one source of an epic's rank. The skill is then used through prosiform: the shared guide states and defines the rules and checks a compiled skill follows, Work Planner's links, hand-offs and entry point conform, every mode compiles within the default budget, and the shared check enforces those rules.

It matters because the skill's history, pull requests and planning have shared a repository with unrelated work, and the workspace that uses it receives a plain copy with no version recorded. One home makes the skill's own changes reviewable on their own, and a pinned submodule makes the installed version a deliberate choice of the workspace that uses it. Prosiform compiles every local link into the bundle an agent reads, and a skill written for a reader who follows links overflows that bundle; links that carry prosiform's meaning keep each mode within it.

## Artifacts

| Artifact | What it holds |
| --- | --- |
| [I16 body](bodies/i16.md) | Initiative body with derived epic dependencies |
| [E05 body](bodies/e05.md) | Check Definitions body with its confirmed joined unit |
| [Decisions](decisions.md) | The user's decisions, the planning decisions taken from them, and the proposed order |
| [Goal trace](goal-trace.md) | Each goal clause traced to its criteria and epics, the ranked gaps and the outside threats |
| [Pair decisions](joins.md) | The rows kept as separate pieces of work, and why |
| [Evidence](evidence.md) | Revisions, the `pf` instrument, bundle sizes per mode, link counts and check callers behind E04 to E07 |
| [Review](review.md) | Each review finding on E04 to E07 and the initiative that carries them, with its resolution |
| [Dependency report](dependencies.txt) | The dependency, joins, contention and priority report over all eight epics |
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
| [E04 W01](e04/w01.md) | Bootstrap and link rules stated |
| [E04 W02](e04/w02.md) | Operator and budget rules stated |
| [E05 W01](e05/w01.md) | Each check defined in the shared guide |
| [E05 W02](e05/w02.md) | Prose names each check by link |
| [E05 W03](e05/w03.md) | Check reports a check named by path |
| [E06 W01](e06/w01.md) | Work Planner links named by section |
| [E06 W02](e06/w02.md) | Modes named in passing as text |
| [E06 W03](e06/w03.md) | Hand-offs dispatched, conditional reads deferred |
| [E07 W01](e07/w01.md) | Entry point bootstraps through prosiform |
| [E07 W02](e07/w02.md) | Every mode compiled within budget |
| [E07 W03](e07/w03.md) | Bundle sizes compared against baseline, delivered by the comparison it records |
| [E07 W04](e07/w04.md) | Check reports link scope and mode reach |
| [E07 W05](e07/w05.md) | Check compiles each mode under budget |

## Links

| Resource | Link |
| --- | --- |
| Initiative | [I16](https://github.com/m2ux/prosiform-skills/issues/1) |
| Skill Cutover | [I16:E00](https://github.com/m2ux/prosiform-skills/issues/2) |
| Workspace Linkage | [I16:E01](https://github.com/m2ux/prosiform-skills/issues/3) |
| Skill Refactor | [I16:E02](https://github.com/m2ux/prosiform-skills/issues/5) |
| Priority Field | [I16:E03](https://github.com/m2ux/prosiform-skills/issues/4) |
| Shared Prosiform Rules | [I16:E04](https://github.com/m2ux/prosiform-skills/issues/6) |
| Check Definitions | [I16:E05](https://github.com/m2ux/prosiform-skills/issues/7) |
| Work Planner Links | [I16:E06](https://github.com/m2ux/prosiform-skills/issues/8) |
| Use Through Prosiform | [I16:E07](https://github.com/m2ux/prosiform-skills/issues/9) |
| Carried-over issue | [m2ux/workflow-server#1595](https://github.com/m2ux/workflow-server/issues/1595) |
| Source of the prosiform evidence | [m2ux/workflow-server#1427](https://github.com/m2ux/workflow-server/issues/1427) |
| Prosiform at the measured revision | [m2ux/prosiform@23882b7d](https://github.com/m2ux/prosiform/tree/23882b7d) |
| Board | [Process: How Work Is Planned and Delivered](https://github.com/users/m2ux/projects/17) |
