# Task 2 implementation report

## Status

COMPLETE — deterministic, non-repetitive idle scheduling is implemented in the
pure Swift core and covered by named dependency-free scheduler checks.

## RED/GREEN evidence

### RED

Added the two specified scheduler checks to
`desktop-cat/Sources/DesktopCatChecks/main.swift`, then ran the focused check
before adding the scheduler implementation:

```text
SDKROOT=/Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
CLANG_MODULE_CACHE_PATH=/private/tmp/desktop-cat-clang-cache \
SWIFTPM_MODULECACHE_OVERRIDE=/private/tmp/desktop-cat-swiftpm-cache \
swift run --disable-sandbox \
  --sdk /Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
  DesktopCatChecks --filter schedulerDoesNotRepeatRecentActivity
```

Result: exit 1. Compilation failed as expected because `CatScheduler` was not
defined (`cannot find 'CatScheduler' in scope`).

### GREEN

Focused checks after implementation:

```text
swift run [same SDK/cache options] DesktopCatChecks --filter schedulerDoesNotRepeatRecentActivity
PASS schedulerDoesNotRepeatRecentActivity
SUMMARY 1 passed, 0 failed

swift run [same SDK/cache options] DesktopCatChecks --filter lateNightBiasAllowsSleeping
PASS lateNightBiasAllowsSleeping
SUMMARY 1 passed, 0 failed
```

Both commands exited 0.

## Implementation

`CatScheduler` now:

- excludes the most recent two activities as cooldown history;
- applies explicit local-hour multipliers for overnight, morning, midday,
  evening, and late-night periods;
- applies mood multipliers for energy, hunger, affection, and playfulness;
- uses injected randomness and normalizes negative or oversized indices with a
  safe modulo operation;
- returns `.sitting` if weighting produces no candidate.

The scheduler API and domain types remain in the dependency-free
`DesktopCatCore` module. The checks use no XCTest or Swift Testing framework.

## Files changed

- `desktop-cat/Sources/DesktopCatCore/Domain/CatScheduler.swift` (new)
- `desktop-cat/Sources/DesktopCatChecks/main.swift` (two named scheduler checks,
  Foundation import for `Date`)

The controller-mandated SwiftPM layout has no `DesktopCatTests` target, so the
brief's framework-test path was represented by the real named checks in
`DesktopCatChecks`.

## Full-suite and production-build verification

Full check suite:

```text
SDKROOT=/Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
CLANG_MODULE_CACHE_PATH=/private/tmp/desktop-cat-clang-cache \
SWIFTPM_MODULECACHE_OVERRIDE=/private/tmp/desktop-cat-swiftpm-cache \
swift run --disable-sandbox \
  --sdk /Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk DesktopCatChecks
```

Result: exit 0.

```text
PASS playfulPersonalityPrefersPlayOverSleep
PASS schedulerDoesNotRepeatRecentActivity
PASS lateNightBiasAllowsSleeping
SUMMARY 3 passed, 0 failed
```

Production build:

```text
SDKROOT=/Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk \
CLANG_MODULE_CACHE_PATH=/private/tmp/desktop-cat-clang-cache \
SWIFTPM_MODULECACHE_OVERRIDE=/private/tmp/desktop-cat-swiftpm-cache \
swift build --disable-sandbox \
  --sdk /Library/Developer/CommandLineTools/SDKs/MacOSX15.4.sdk
```

Result: exit 0; `Build complete! (1.99s)`.

`git diff --check` also passed.

## Self-review

- The scheduler is pure Swift and has no UI, persistence, network, or global
  activity logging concerns.
- All random selection goes through the injected closure; modulo normalization
  prevents out-of-range array access, including negative indices.
- Recent-history exclusion is applied before weighting, and empty candidates
  safely fall back to `.sitting`.
- Time-of-day and mood multipliers are explicit and separate from personality
  weights.
- The existing personality check remains green, and the package production
  build links successfully.

## Concerns

- The controller's dependency-free harness replaces the original XCTest file
  requirement because XCTest/Testing are unavailable in this environment; no
  framework-based test target was added.
- `now` is currently used for local-hour weighting; cooldown state is carried by
  the supplied recent-activity history because the interface provides no
  per-activity timestamps.
