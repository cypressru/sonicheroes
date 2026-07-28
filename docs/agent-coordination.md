# Agent coordination

Updated 2026-07-28 by Codex against upstream `0602d41`.

Check this file and the upstream open-PR list before starting a TU. Update the
table when claiming or handing off work so parallel agents do not duplicate it.

## Current ownership

| Owner | Scope | Branch / PR | State |
| --- | --- | --- | --- |
| ThePlayerRolo | AutoSaveD rework | upstream PR #116 (`main`) | Active |
| Claude Code | GX graphics library | External agent branch | Active; reserved |
| Codex + agents | Complete original `game/skyfs_adx.c` TU (`0x80013038`–`0x80014154`) | `pr-skyfs-adx` planned | Active; 19 functions, complete section layout proven; 17 functions exact and the final real code difference is two register-allocation instructions in `skyFread` |
| Codex agents | Complete original `Peripheral.cpp` TU (`0x80014154`–`0x80015AC0`) | Branch deferred until 100% | Paused behind `skyfs_adx.c`; 19/20 functions exact, final function differs by four register-choice instructions |

The unified C++ AdvertiseD reconstruction supersedes the older fragmented C
branches. Do not claim or update those fragments: all 434 functions across its
21 objects are exact on `pr-advertised`.

The earlier `pr-module-loader` branch is also superseded and must not be opened
or merged as a standalone PR. Debug-source provenance and whole-object compiler
behavior prove that its range, the adjacent DVD-status functions, state setter,
and RenderWare file callbacks are one original `skyfs_adx.c` translation unit.

## Ready for PR

| Owner | Scope | Branch | Verification |
| --- | --- | --- | --- |
| Codex | AdvertiseD overlay | `pr-advertised` | 434/434 functions across 21 objects 100%; exact REL/DOL and full-build gates pass |

## Recently integrated

The prior Codex SDK branches (`pr-nubinit`, `pr-nubevent`,
`pr-dolphin-trk`, `pr-targimpl`, and `pr-osaudiosystem`) are present in
upstream history. The current upstream report has all 84 configured SDK TUs and
all 730 SDK functions at 100%.

## PR conventions

- One complete original file or coherent original tree per PR; do not split a
  source file at convenient address boundaries.
- Branches use `pr-*`.
- Prefer C++ unless the original file is positively identified as C.
- Replace address-based names with evidence-backed names; mark guesses.
- Keep the implementation in C or C++ unless matching is demonstrably
  impossible without assembly.
- Do not flip a TU to `Matching` until every function and section is exact and
  the fresh-build, link, and SHA-1 gates pass.
- Use one checkout and one active build where practical. Do not create fleets of
  worktrees or unbounded permutation outputs.
