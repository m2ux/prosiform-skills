# I16 Pair Decisions, 2 November 2026

This record states why candidate units stay split or join.

- E01:W03 and E01:W04: separate. They change different repositories, prosiform's workspace and workflow-server's template, and the template's removal waits for prosiform's link so prosiform never has neither copy.
- E01:W01 and E01:W02: separate. Each changes its own template script and carries its own fixture test, so either merges without waiting on the other.
- E02:W01 and E02:W02: separate. One changes the skill's commands and its tests, the other the shared check and its tests, and each suite verifies its own change.
- E07:W01 and E07:W03: separate. The entry point's bootstrap is verified by a walk, the mode cuts by each mode's compile, and neither change reads the other.
- E07:W04 and E07:W05: separate. The bundle comparison is a record committed to `engineering` and takes no pull request.
- E07:W04 and E07:W06: separate. The bundle comparison is a record committed to `engineering` and takes no pull request.

## Joined Units, 5 November 2026

- E05:W01 and E05:W02: joined. Both extend main:guidelines.md. One pull request orders the definitions and their prose callers and waits for E02:W01 and E02:W02, as the user confirms.
