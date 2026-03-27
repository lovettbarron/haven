---
phase: 05-documentation-and-guides
plan: 02
subsystem: documentation
tags: [troubleshooting, crop-tiers, plant-care, severity-system, danish-climate]

# Dependency graph
requires:
  - phase: 02-spring-planting
    provides: planting grids for beds A-E with all crop positions
  - phase: 03-warm-season-planting
    provides: warm-season crop selections and bed assignments
provides:
  - Symptom-based troubleshooting guide with severity system and crop index
  - Three-tier crop difficulty classification for all 27 varieties
affects: [05-03-neighbor-vacation-guide, 06-physical-delivery]

# Tech tracking
tech-stack:
  added: []
  patterns: [symptom-based-lookup, severity-emoji-system, crop-difficulty-tiers]

key-files:
  created:
    - docs/troubleshooting-guide.md
    - docs/crop-difficulty-tiers.md
  modified: []

key-decisions:
  - "Aphid watch-and-wait is the #1 featured entry in the troubleshooting guide, not buried among other symptoms"
  - "Tumbling Tom classified as Needs Care (pot drying risk) rather than Can't Fail despite being a compact variety"
  - "Garlic included in difficulty tiers (Year 2 Challenge) even though not yet planted, with bed TBD"
  - "Mint classified as Needs Care because pot containment changes its care profile from the invasive-easy it would be in ground"

patterns-established:
  - "Severity system: green/yellow/red emoji + timeframe (No rush / This week / Today)"
  - "Crop index format: alphabetical table with bed, position, and cross-referenced common issues"
  - "Difficulty tier format: per-crop entry with bed, rationale, failure mode, and cross-references"

requirements-completed: [DOCS-02, DOCS-03]

# Metrics
duration: 13min
completed: 2026-03-27
---

# Phase 5 Plan 2: Crop Knowledge References Summary

**Symptom-based plant doctor guide with green/yellow/red severity system and three-tier crop difficulty classification covering all 27 garden varieties**

## Performance

- **Duration:** 13 min
- **Started:** 2026-03-27T06:25:33Z
- **Completed:** 2026-03-27T06:39:09Z
- **Tasks:** 2
- **Files created:** 2

## Accomplishments
- Troubleshooting guide covers 10 symptom categories with severity labels, child action steps, and 25 photo placeholders
- Aphid watch-and-wait philosophy prominently featured as entry #1, explaining the borage/nasturtium/calendula predator attraction design
- Crop index appendix lists all 27 varieties with bed assignments, positions, and cross-referenced common issues
- Difficulty tiers classify 13 Can't Fail + 11 Needs Care + 4 Year 2 Challenge crops with bed assignments and risk assessments
- Summary table provides single-view reference of all crops, tiers, beds, and key risks

## Task Commits

Each task was committed atomically:

1. **Task 1: Create symptom-based troubleshooting guide** - `f2b15b6` (feat)
2. **Task 2: Create difficulty-tiered crop classification** - `d43e076` (feat)

## Files Created/Modified
- `docs/troubleshooting-guide.md` - Symptom-based plant doctor with severity system, 10 symptom categories, and crop index appendix for all 27 varieties
- `docs/crop-difficulty-tiers.md` - Three-tier crop difficulty classification with per-crop entries, bed assignments, care notes, and summary table

## Decisions Made
- Aphid entry placed as #1 in the guide (not alphabetical) to match its prominence in the garden's pest management philosophy
- Tumbling Tom classified as Needs Care rather than Can't Fail -- pot drying is a real risk that differentiates it from in-ground growing
- Garlic included in difficulty tiers with "TBD" bed assignment since it will be planted in autumn 2026
- Mint classified as Needs Care (pot watering needs) rather than Can't Fail (which it would be in-ground)
- Blossom End Rot and Runner Management included as standalone symptom sections beyond the minimum required categories

## Deviations from Plan

None - plan executed exactly as written.

## Issues Encountered
- Previous execution attempt was interrupted by API error; troubleshooting guide existed but was uncommitted. Verified content against plan requirements before committing.

## User Setup Required

None - no external service configuration required.

## Next Phase Readiness
- Both crop knowledge documents complete and cross-referenced to each other and to planting grids
- Ready for Plan 03 (neighbor vacation guide) which can reference both documents
- Photo placeholders (25 in troubleshooting guide) ready for in-season replacement

---
*Phase: 05-documentation-and-guides*
*Completed: 2026-03-27*
