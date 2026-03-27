---
phase: 06-vacation-preparation
plan: 01
subsystem: docs
tags: [reservoir, mulching, vacation, testing-protocol, moisture-retention]

# Dependency graph
requires:
  - phase: 01-bed-infrastructure
    provides: reservoir-build.md with capacity specs (15-20L, 2-4 day autonomy)
provides:
  - 5-day reservoir test protocol with daily log template
  - Per-bed mulching guide with material assignments and volume calculations
affects: [06-02-PLAN, pre-departure-checklist, neighbor-vacation-guide]

# Tech tracking
tech-stack:
  added: []
  patterns: [printable daily log template, per-bed instruction cards]

key-files:
  created:
    - docs/reservoir-test-protocol.md
    - docs/mulching-guide.md
  modified: []

key-decisions:
  - "Reservoir test written generically for 'each bed with a reservoir' due to bed identity discrepancy between CLAUDE.md and data files"
  - "Terrace beds D/E recommended at 8cm depth (upper end of 5-8cm range) due to wind exposure and faster drying"

patterns-established:
  - "Physical test protocol format: overview, procedure, printable log template, pass/fail criteria, fallback"

requirements-completed: [VACN-01, VACN-02]

# Metrics
duration: 2min
completed: 2026-03-27
---

# Phase 6 Plan 01: Reservoir Test Protocol and Mulching Guide Summary

**5-day reservoir dry-run test protocol with daily finger-test log, plus per-bed mulching guide with straw/bark material assignments and volume calculations for all 5 beds**

## Performance

- **Duration:** 2 min
- **Started:** 2026-03-27T07:08:01Z
- **Completed:** 2026-03-27T07:09:30Z
- **Tasks:** 2
- **Files modified:** 2

## Accomplishments
- Reservoir test protocol with 5-day procedure, child-led finger test, printable daily log, pass/fail criteria, and failure fallback (increase neighbor visits)
- Mulching guide covering all 5 beds with correct material assignments (straw A/B/C, bark D/E), volume table, shopping quantities (2 straw bales + 1x50L bark), and child activity framing

## Task Commits

Each task was committed atomically:

1. **Task 1: Create reservoir test protocol** - `0bf3f3d` (feat)
2. **Task 2: Create mulching guide** - `b041b7c` (feat)

## Files Created/Modified
- `docs/reservoir-test-protocol.md` - 5-day dry-run test procedure with daily log template and pass/fail criteria
- `docs/mulching-guide.md` - Per-bed mulching instructions with material types, depth targets, volume calculations, and shopping list

## Decisions Made
- Reservoir test written generically ("for each bed with a reservoir installed") rather than naming specific beds, due to the mapping discrepancy between CLAUDE.md (A and B) and data files (bed-c). User confirms on test day.
- Terrace beds D/E recommended at 8cm depth (upper end of range) to compensate for wind exposure and smaller soil volume.

## Deviations from Plan

None - plan executed exactly as written.

## Issues Encountered
None.

## User Setup Required
None - no external service configuration required.

## Next Phase Readiness
- Both preparation documents ready for Plan 06-02 (pre-departure countdown script and printable checklist)
- Mulching guide referenced by Day -3 of the countdown
- Reservoir test protocol should be executed by W26 (independent of the countdown)

---
*Phase: 06-vacation-preparation*
*Completed: 2026-03-27*
