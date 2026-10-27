# Sill

Open-source, free app that streams a Mac window or desktop to iPhone and iPad,
with a free Mac companion. Tip jar, no subscription, no servers. Read
[the brief](docs/BRIEF.md) before product-level work; it records the original
scope and dated decisions. Formerly winstream.

[AGENTS.md](AGENTS.md) is a relative symlink to this file, the canonical project
rule source. Edit CLAUDE.md rather than maintaining a second copy.
[The documentation index](docs/README.md) routes the other knowledge.

## Working with the user

- Ask the user before important architectural or product decisions.
- Do not assume answers to unanswered questions or implement a fallback without
  approval. When user input is required, stop the turn and wait for their reply.

## Current step

Use [README](README.md) for current features and
[Developing Sill](docs/DEVELOPMENT.md) for behavior, limitations and test tools.
[Dated implementation records](docs/implementation-history.md) describe earlier
work and tests, not a current backlog or a verified live release.

## Layout

[Developing Sill, Overview](docs/DEVELOPMENT.md#overview) describes the modules.
[Source map and test hooks](docs/agent-reference.md#layout) retains the detailed
file-by-file reference. Check the named code before editing it.

- `Sources/StreamProtocol`: shared wire format.
- `Sources/SillHost`, `SillHostCLI`, `SillMenuBar`: Mac core and its entry points.
- `iOSClient`: device app; `Tests/checks`: pure rules compiled from app sources.
- `docs`: guides and design evidence; `site`: static website sources.

## Build and run

```sh
swift build -c release
Tests/checks/run-all.sh                 # append names for a focused run
Scripts/make-app.sh                     # builds .build/Sill.app
```

Xcode 27 is used for the Mac; the iOS app needs Xcode 27.1 or later.
[Developing Sill](docs/DEVELOPMENT.md#build-and-run) has setup and permissions;
[the test reference](docs/agent-reference.md#build-and-run) has detailed recipes.
Keep test output under `.build/`. Follow the development guide's isolation
recipes before running a host or simulator against a live session.
Installing or opening the app, posting input, resetting settings and publishing
are separate actions; a documented command is not authorization to run it.

## Compatibility floor

Follow [Protocol compatibility](docs/protocol-compatibility.md). It preserves the
peer contract, including old ALPNs, message kinds and payloads. Shared wire types
live in `Sources/StreamProtocol`; new fields must remain optional and older peers
must either work or receive the documented update refusal.

## Conventions

- Swift, Apple frameworks only. No third-party dependencies unless a decision
  in `docs/BRIEF.md` says so. Zero operating costs is a hard rule.
- Threading in the spike is by hand: capture queue → VT callback thread →
  network queue. Keep it explicit and commented rather than reaching for actors
  until the design settles.
- HEVC, no B-frames, real-time mode. AV1 is out (no hardware encode on Apple
  silicon as far as we know).
- Latency beats quality. Drop frames before queuing them.
- Don't add features the current milestone doesn't need.

## Decisions already made (don't relitigate without asking Noah)

- Free app, tip jar, open source. Not paid, not subscription.
- iCloud auto-pairing was planned for milestone 5; it is not implemented in this
  checkout. Current pairing uses Bonjour discovery and TLS with a scanned or typed
  code, or automatic pairing over the USB cable (docs/DEVELOPMENT.md, Pairing at
  home). This status does not decide whether to pursue iCloud pairing later.
- Native feel is the bar: Flighty-level polish, iOS conventions, Duo layouts.
- License: Apache-2.0, LICENSE since PR #15, kept when the repository went
  public on 2026-09-26 (paid plan is gone, so no GPL/CLA needed).
- v1 out of scope: hole punching, multi-window, layout customization. Audio is in scope since
  2026-09-27 (Noah: "Audio: the plan is done and parked as a v2 feature by your earlier decision",
  first in what he wanted worked on; docs/audio-plan.md, docs/BRIEF.md), and in, as a beta, since
  2026-10-20 (Noah, about PR #94: "merge as beta support"): Send Audio, on by default in Sill.app
  since 2026-10-27; the CLI's `--audio` still opts in. Since
  2026-10-27 (Noah: "Sound should be a toggle in the settings menu") the Mac's menu and Settings and
  a device's Settings panel set it for every device, and each device's Mute is its own; no Sound
  button in the bar.
