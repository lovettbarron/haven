# Project Retrospective

*A living document updated after each milestone. Lessons feed forward into future planning.*

## Milestone: v1.0 — Foundation Season

**Shipped:** 2026-03-28
**Phases:** 6 | **Plans:** 15

### What Was Built
- 2 raised bed designs with construction guides, soil recipes, slug defense, and reservoir build
- Spring and warm-season planting plans with cm-level grid maps for both beds
- ADHD-adapted planting session scripts with sensory transitions and break points
- JSON data system: 27 crop files, 30 weekly schedules, HA entity schemas
- Property visualization, troubleshooting guide, difficulty tiers, neighbor vacation guide
- Pre-departure vacation protocol with reservoir testing and mulching guides

### What Worked
- Parallel execution of data/docs phases alongside physical planting phases
- JSON-first approach meant HA schemas were ready before sensors arrived
- Companion planting research paid off with clean bed layouts
- Session scripts with ADHD adaptations (breaks, transitions, concrete tasks)

### What Was Inefficient
- Bed numbering (1-5) didn't match final planting assignments (A-E) -- caused v1.1 rework
- 5-bed design was simplified to 2 beds mid-project -- some docs written for 5 beds needed updating
- Some requirements overlapped (DOCS-06/INFRA-07 both cover shopping lists)

### Patterns Established
- Bed A-E canonical naming (resolved in v1.1)
- haven_ prefix for all HA entities
- ISO week numbering (W16, W20, etc.) throughout
- JSON schemas for all structured data

### Key Lessons
1. Finalize physical layout before writing detailed docs -- bed remapping caused cascade of fixes
2. 2-bed garden is the right scope for year 1 -- simpler to maintain, lower cognitive load for child
3. Session scripts need "meltdown exit ramps" not just break points

---

## Milestone: v1.1 — Gap Closure and Operational Readiness

**Shipped:** 2026-03-30
**Phases:** 6 | **Plans:** 10

### What Was Built
- Canonical bed identity (A-E) applied across all docs, JSON, and HA configs
- Daily routine card and weekly garden walk (printable, ADHD-adapted, bilingual)
- Between-session treasure hunts and photo log approach
- Spring planting shopping list with purchase priority timeline and tool inventory
- Complete HA setup walkthrough with copy-paste YAML (sensors, automations, dashboard)
- End-of-season guide, perennial care reference, soil refresh protocol, season review template
- Crop failure recovery section in troubleshooting guide
- Vacation flags in W30-W33 schedules, garlic alignment in W40

### What Worked
- Gap analysis (quick task #1) effectively identified all rework needed
- Phase 7 (identity fix) as foundation for all subsequent phases was correct ordering
- Combining related requirements into single documents (CENG-02 + CENG-04)
- Planning artifact maintenance as final phase caught self-referential staleness

### What Was Inefficient
- Phase 12 had a meta-problem: fixing its own checkboxes creates new checkboxes to fix
- Nyquist validation was partial for 11/12 phases -- systematic gap in the workflow
- SUMMARY.md one_liner field never populated -- extraction tooling returned N/A

### Patterns Established
- bed_notes field for documenting exclusion rationale on crop JSON files
- vacation_note as optional schema field for context-specific schedule metadata
- Danish cues as father-spoken prompts (not child-readable text)
- Pick-2-of-4 model for child choice and agency in activities

### Key Lessons
1. Self-referential maintenance phases should be the very last thing done -- and accept they'll always have a small meta-gap
2. Budget estimates need to be updated when scope changes (2,000-5,000 DKK → 8,500-10,500 DKK after corten decision)
3. Human verification items (print layouts, live HA testing) are a natural boundary -- don't block milestone completion on them

### Cost Observations
- Model mix: ~80% sonnet, ~15% haiku, ~5% opus (research phases)
- Sessions: ~8-10 across both milestones
- Notable: 25 plans completed in ~4 calendar days -- documentation-heavy project executes fast

---

## Cross-Milestone Trends

### Process Evolution

| Milestone | Phases | Plans | Key Change |
|-----------|--------|-------|------------|
| v1.0 | 6 | 15 | Established project structure and conventions |
| v1.1 | 6 | 10 | Gap-driven cleanup, operational readiness |

### Top Lessons (Verified Across Milestones)

1. Finalize physical layout decisions before writing detailed documentation -- changes cascade
2. Human verification items (printing, live testing) are a natural boundary between planning and execution
3. JSON-first data approach enables future integrations without rework
