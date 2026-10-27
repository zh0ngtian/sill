# Documentation

## Current guides

| Need | Read |
|---|---|
| What Sill does, requirements and building from source | [Project README](../README.md) |
| Development, settings, permissions, test hooks and limitations | [Developing Sill](DEVELOPMENT.md) |
| Agent entry point and project constraints | [AGENTS.md](../AGENTS.md); [CLAUDE.md](../CLAUDE.md), Compatibility floor, Conventions and Decisions already made |
| Wire changes and compatibility guarantees | [Protocol compatibility](protocol-compatibility.md) |
| Detailed file map and test recipes | [Source map and test hooks](agent-reference.md) |
| Release procedures | [Release checklist](release-checklist.md) |
| App Store copy and review material | [App Store metadata](app-store-metadata.md) |
| Reporting a vulnerability | [Security policy](../SECURITY.md) |
| Pure checks and simulator input tools | [Checks](../Tests/checks/README.md), [duorig](../Tests/duorig/README.md), [keyrig](../Tests/keyrig/README.md) |
| Icons, download artwork and screenshots | [Design sources](../design/README.md) |

CLAUDE.md is the canonical project rule source. AGENTS.md is a relative symlink
to it; edit CLAUDE.md to keep both agent entry points in sync.

The code and configuration decide what this checkout implements. README and
DEVELOPMENT describe that behavior; a local build or an old release note does
not establish which version is live on the website or in the App Store.
The release checklist and metadata contain dated release records and draft
material: verify the external state before using them to claim a release is live.

## Design and implementation records

[The product brief](BRIEF.md) records the original scope and decisions. The
plans below preserve designs, tradeoffs, compatibility details and dated test
evidence. They are retained for that purpose, not as an active task queue.
[Implementation history](implementation-history.md) holds the dated development
and verification entries formerly kept in CLAUDE.md.
An old branch name, worktree path, line number, open question or instruction
to resume work describes the recorded stage. Re-read the affected code and the
current guides before using it. A proposed default is not user approval.
Historical scratch paths may belong to another machine and are not prerequisites
for building this checkout. An unperformed device test remains unverified.

| Topic | Design and evidence |
|---|---|
| Mac menu bar app and packaging | [Menu bar app](menu-bar-app-plan.md) |
| Device controls for host settings | [Host settings](ipad-host-settings-plan.md) |
| Peer-to-peer discovery and transport | [Direct Wireless Connection](direct-wireless-plan.md) |
| VPN and public-address connections | [Remote access](remote-access-plan.md) |
| Quality, pacing and returning home | [Away from home](remote-bundle-plan.md) |
| Home TLS, pairing and cable recognition | [Pairing at home](home-pairing-plan.md) |
| Identity storage and signing | [Keychain](keychain-plan.md) |
| Update feed and peer compatibility notices | [Update notices](update-notice-plan.md) |
| Mac menus on the device | [Menu mirroring](menu-bar-plan.md) |
| Pointer capture and visibility | [Pointer visibility](pointer-visibility-plan.md) |
| iPhone portrait geometry | [Portrait layout](iphone-portrait-plan.md) |
| More picture space on iPhone | [Larger Picture](larger-picture-plan.md) |
| Hinge and fold layouts | [iPhone Duo](iphone-duo-plan.md) |
| Onboarding and replaying the tour | [Walkthrough](first-run-walkthrough-plan.md) |
| Three-finger gestures | [Trackpad gestures](trackpad-gestures-plan.md) |
| Hardware keyboard and scrolling | [Hardware keyboard](hardware-keyboard-plan.md) |
| Clipboard subscription and privacy | [Clipboard](clipboard-plan.md) |
| Sound transport and playback; beta acceptance tests | [Audio](audio-plan.md) |
| Discovery after suspension | [Reconnect after sleep](reconnect-after-sleep-plan.md) |
| Returning resized windows to their original frames | [Window restoration](restore-window-frames-plan.md) |
| Mac Settings on small screens | [Settings window](settings-window-plan.md) |

For the current Show Trackpad behavior and its interaction with Larger Picture,
use [the iOS app section](DEVELOPMENT.md#the-ios-app). The portrait and Larger
Picture plans' original measurements describe the arrangements they name.
