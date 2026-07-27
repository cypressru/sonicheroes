# Agent coordination

Updated 2026-07-27 by Codex against upstream `e4d6579`.

Check this file and the upstream open-PR list before starting a TU. Update the
table when claiming or handing off work so parallel agents do not duplicate it.

## Current ownership

| Owner | Scope | Branch / PR | State |
| --- | --- | --- | --- |
| ThePlayerRolo | AutoSaveD rework | upstream PR #116 (`main`) | Active |
| Codex | `advertiseD/slot_query.c` | `pr-advertise-slot-query` | Claimed next |

The upstream report at `e4d6579` had three remaining configured game functions:
one each in `advertiseD/demo_object.c`, `advertiseD/slot_query.c`, and
`autosaveD/widget_slices.c`. AutoSaveD is reserved while PR #116 is active.

## Ready for PR

| Owner | Scope | Branch | Verification |
| --- | --- | --- | --- |
| Codex | `advertiseD/demo_object.c` | `pr-advertise-demo-object` | 3/3 functions and `.text` 100%; REL link and 18-file SHA-1 gate pass |

## Recently integrated

The prior Codex SDK branches (`pr-nubinit`, `pr-nubevent`,
`pr-dolphin-trk`, `pr-targimpl`, and `pr-osaudiosystem`) are present in
upstream history. The current upstream report has all 84 configured SDK TUs and
all 730 SDK functions at 100%.

## PR conventions

- One file or coherent tree per PR.
- Branches use `pr-*`.
- Replace address-based names with evidence-backed names; mark guesses.
- Keep the implementation in C or C++ unless matching is demonstrably
  impossible without assembly.
- Do not flip a TU to `Matching` until every function and section is exact and
  the fresh-build, link, and SHA-1 gates pass.
- Use one checkout and one active build where practical. Do not create fleets of
  worktrees or unbounded permutation outputs.
