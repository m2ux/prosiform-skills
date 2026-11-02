# I16 Pair Decisions, 2 November 2026

Each line records one pair of rows: joined into one pull request, or kept as separate pieces of work.

- E00:W00 and E00:W02: separate. W00 is pushed directly as `main`'s first history before any epic base exists, and W02 is a pull request into the base cut from that history.
- E01:W03 and E01:W04: joined. The template adds the submodule link and deletes the plain copy in one pull request, so no fork of the template ever has neither copy.
