# Agent coordination

Updated 2026-07-28 by Codex against upstream `0602d41`.

Check this file and the upstream open-PR list before starting a TU. Update the
table when claiming or handing off work so parallel agents do not duplicate it.

## Current ownership

| Owner | Scope | Branch / PR | State |
| --- | --- | --- | --- |
| ThePlayerRolo | AutoSaveD rework | upstream PR #116 (`main`) | Active |
| Claude Code | GX graphics library | External agent branch | Active; reserved |
| Codex | `game/skyfs_adx.c` / `dlfs.c` (`0x80013398`–`0x80014154`) | `pr-skyfs-adx` planned | Active; 11/12 functions exact, final function differs by two register allocations |
| Codex agents | Complete original `Peripheral.cpp` TU (`0x80014154`–`0x80015AC0`) | Branch deferred until 100% | Active; 19/20 functions exact, final function differs by four register-choice instructions |

The unified C++ AdvertiseD reconstruction supersedes the older fragmented C
branches. Do not claim or update those fragments: all 434 functions across its
21 objects are exact on `pr-advertised`.

## Ready for PR

| Owner | Scope | Branch | Verification |
| --- | --- | --- | --- |
| Codex | `game/module_loader.cpp` | `pr-module-loader` | 4/4 functions and all owned sections 100%; full build and DOL SHA-1 gate pass |
| Codex | AdvertiseD overlay | `pr-advertised` | 434/434 functions across 21 objects 100%; exact REL/DOL and full-build gates pass |

## Recently integrated

The prior Codex SDK branches (`pr-nubinit`, `pr-nubevent`,
`pr-dolphin-trk`, `pr-targimpl`, and `pr-osaudiosystem`) are present in
upstream history. The current upstream report has all 84 configured SDK TUs and
all 730 SDK functions at 100%.

## PR conventions

- One file or coherent tree per PR.
- Branches use `pr-*`.
- Prefer C++ unless the original file is positively identified as C.
- Replace address-based names with evidence-backed names; mark guesses.
- Keep the implementation in C or C++ unless matching is demonstrably
  impossible without assembly.
- Do not flip a TU to `Matching` until every function and section is exact and
  the fresh-build, link, and SHA-1 gates pass.
- Use one checkout and one active build where practical. Do not create fleets of
  worktrees or unbounded permutation outputs.
