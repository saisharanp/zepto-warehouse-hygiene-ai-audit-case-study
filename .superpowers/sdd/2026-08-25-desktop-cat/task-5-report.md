# Task 5 implementation report

## Status

Implemented the desktop overlay bridge and conservative workspace protection in
the controller-mandated SwiftPM layout. The `DesktopCatCore` module now owns a
main-actor AppKit panel controller and a workspace observer; the dependency-free
runner covers all testable geometry and fullscreen-classification behavior.

## RED/GREEN evidence

### RED

Added the five named desktop checks to
`desktop-cat/Sources/DesktopCatChecks/main.swift` before any Task 5 production
source existed, then ran:

```text
SDKROOT=/Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
CLANG_MODULE_CACHE_PATH=/private/tmp/desktop-cat-clang-cache \
SWIFTPM_MODULECACHE_OVERRIDE=/private/tmp/desktop-cat-swiftpm-cache \
swift run --disable-sandbox \
  --sdk /Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
  DesktopCatChecks --filter positionIsClampedInsideVisibleFrame
```

Result: exit 1 during harness compilation, as intended. The compiler reported
that `DesktopCatWindowController`, `WorkspaceObserver`, and `WorkspaceWindow`
were not in scope. The initial test compilation also identified that the check
target needed its normal `CoreGraphics` import; that test-only import was added
before implementing either production file.

### GREEN

After implementing the panel controller and observer, fresh focused checks
passed:

```text
PASS positionIsClampedInsideVisibleFrame
SUMMARY 1 passed, 0 failed

PASS oversizedWindowIsAnchoredToVisibleFrameOrigin
SUMMARY 1 passed, 0 failed

PASS fullscreenClassificationRecognizesScreenCoveringWindow
PASS fullscreenClassificationIgnoresNonCoveringOrNonContentWindows
PASS fullscreenClassificationHidesWhenDataIsUnavailable
SUMMARY 3 passed, 0 failed
```

Each invocation used the same macOS 15.4 SDK/cache command prefix shown in the
RED command and exited 0.

## Implementation

### DesktopCatWindowController

- Creates a transparent, borderless, non-activating `NSPanel` with no shadow,
  background moving, and an `EmptyView` SwiftUI hosting root for Task 6 to
  replace.
- Supports desktop and floating levels, click-through via
  `ignoresMouseEvents`, and explicit show/hide operations.
- Restores the persisted screen-relative position against the main visible
  frame and clamps it. Display-parameter changes clamp the current panel to a
  visible frame again.
- Hides itself when the associated workspace observer reports fullscreen;
  uncertainty is therefore safe by default.

### WorkspaceObserver

- Subscribes to active-application notifications and refreshes fullscreen
  state on the main actor.
- Inspects only the frontmost process's on-screen, layer-zero window-server
  records. It does not request Accessibility permission or capture input.
- Separates that data collection from the public pure
  `isFullscreenAppActive(windowData:screenFrames:)` classifier. Missing window
  data or screen data returns `true`, which hides the cat conservatively.

## Files changed

- `desktop-cat/Sources/DesktopCatCore/Desktop/DesktopCatWindowController.swift`
  (new)
- `desktop-cat/Sources/DesktopCatCore/Desktop/WorkspaceObserver.swift` (new)
- `desktop-cat/Sources/DesktopCatChecks/main.swift` (five named checks)
- `.superpowers/sdd/2026-08-25-desktop-cat/task-5-report.md` (this report)

No XCTest or Swift Testing source was added. The binding controller ruling
supersedes the obsolete XCTest file path in the task brief.

## Full-suite and production-build verification

Full check suite:

```text
SDKROOT=/Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
CLANG_MODULE_CACHE_PATH=/private/tmp/desktop-cat-clang-cache \
SWIFTPM_MODULECACHE_OVERRIDE=/private/tmp/desktop-cat-swiftpm-cache \
swift run --disable-sandbox \
  --sdk /Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
  DesktopCatChecks
```

Result: exit 0, `SUMMARY 21 passed, 0 failed`.

Production build:

```text
SDKROOT=/Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
CLANG_MODULE_CACHE_PATH=/private/tmp/desktop-cat-clang-cache \
SWIFTPM_MODULECACHE_OVERRIDE=/private/tmp/desktop-cat-swiftpm-cache \
swift build --disable-sandbox \
  --sdk /Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk
```

Result: exit 0; `Build complete! (1.82s)`.

`git diff --check` also exited 0 before commit.

## Manual verification

No UI automation was used. The current `DesktopCatApp` intentionally remains a
minimal Settings scene and does not yet own the controller lifecycle or cat
renderer; those are Task 6 integration work. Consequently, launching the app
cannot create this otherwise empty panel for a meaningful visible manual
inspection without exceeding the requested scope. The pure checks cover
clamping and fullscreen decisions without opening a window. Manual confirmation
of panel transparency, click-through, dragging across real displays, and live
fullscreen transitions remains for the Task 6-integrated app.

## Self-review

- `DesktopCatWindowController` is `@MainActor`; all AppKit panel state and
  display-notification handling stay at the desktop/system boundary.
- The controller has no cat renderer, controls, network access, analytics,
  cloud storage, Accessibility request, global activity logging, or input
  capture.
- The fullscreen classifier only treats a window as fullscreen when it is both
  on screen and layer zero and covers an available screen frame. Missing
  collection data or no screen data intentionally returns `true`.
- The clamp handles a panel larger than a visible frame by anchoring it to that
  frame's origin instead of producing an out-of-bounds maximum.
- The named checks exercise real static geometry/classification behavior with
  literal frames; no mocks or visible windows are needed.

## Concerns

SwiftPM emits pre-existing user-level cache warnings because its default cache
locations are not writable in this environment. The mandated writable module
caches and macOS 15.4 SDK still produce successful checks and a successful
production build. Live panel behavior awaits Task 6 lifecycle integration, as
noted above.

## Fix round 1/5

### Changed behavior

- `WorkspaceObserver` now refreshes on both active-application and active-space
  changes. Native fullscreen entry or exit by the already-frontmost app can
  therefore refresh the conservative visibility state without an application
  activation event.
- Fullscreen classification now requires an on-screen, layer-zero window frame
  to match a screen frame within an explicit one-point tolerance for origin and
  size. A spanning window no longer qualifies merely because it contains a
  display.
- Window-server collection excludes the current process ID, preserving the
  different-application scope even if this app becomes frontmost.

### RED/GREEN evidence

Added these real, pure classification checks before changing production code:

- `fullscreenClassificationAllowsSmallFrameTolerance`
- `fullscreenClassificationRejectsSpanningWindow`

RED command:

```text
SDKROOT=/Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
CLANG_MODULE_CACHE_PATH=/private/tmp/desktop-cat-clang-cache \
SWIFTPM_MODULECACHE_OVERRIDE=/private/tmp/desktop-cat-swiftpm-cache \
swift run --disable-sandbox \
  --sdk /Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
  DesktopCatChecks --filter fullscreenClassification
```

Output (exit 1):

```text
PASS fullscreenClassificationRecognizesScreenCoveringWindow
FAIL fullscreenClassificationAllowsSmallFrameTolerance: expected a window within frame tolerance to be fullscreen
FAIL fullscreenClassificationRejectsSpanningWindow: expected a spanning window not to be classified as fullscreen
PASS fullscreenClassificationIgnoresNonCoveringOrNonContentWindows
PASS fullscreenClassificationHidesWhenDataIsUnavailable
SUMMARY 3 passed, 2 failed
```

After adding the active-space observer, one-point frame matcher, and
self-process exclusion, the same focused command produced (exit 0):

```text
PASS fullscreenClassificationRecognizesScreenCoveringWindow
PASS fullscreenClassificationAllowsSmallFrameTolerance
PASS fullscreenClassificationRejectsSpanningWindow
PASS fullscreenClassificationIgnoresNonCoveringOrNonContentWindows
PASS fullscreenClassificationHidesWhenDataIsUnavailable
SUMMARY 5 passed, 0 failed
```

### Full verification

Full runner command:

```text
SDKROOT=/Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
CLANG_MODULE_CACHE_PATH=/private/tmp/desktop-cat-clang-cache \
SWIFTPM_MODULECACHE_OVERRIDE=/private/tmp/desktop-cat-swiftpm-cache \
swift run --disable-sandbox \
  --sdk /Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
  DesktopCatChecks
```

Output: exit 0, `SUMMARY 23 passed, 0 failed`.

Production build command:

```text
SDKROOT=/Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
CLANG_MODULE_CACHE_PATH=/private/tmp/desktop-cat-clang-cache \
SWIFTPM_MODULECACHE_OVERRIDE=/private/tmp/desktop-cat-swiftpm-cache \
swift build --disable-sandbox \
  --sdk /Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk
```

Output: exit 0; `Build complete! (1.82s)`.

### Fix-round self-review

The pure checks reject a window that encloses a display but has a materially
different frame, and accept a frame differing only by half a point. The
window-server query remains scoped to the frontmost PID, now explicitly rejects
the current PID, and still returns `nil` (which hides the cat) when collection
data cannot be read. `activeSpaceDidChangeNotification` is observed alongside
application activation; both callbacks refresh on the main actor.
