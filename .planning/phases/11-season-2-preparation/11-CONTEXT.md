# Phase 11: Season 2 Preparation - Context

**Gathered:** 2026-03-28
**Status:** Ready for planning

<domain>
## Phase Boundary

Documentation for everything after the growing season ends -- cleanup, perennial care, soil refresh, lessons learned, and crop failure recovery -- so the family is not stranded at W44. Covers SSN2-01 through SSN2-05. Garlic autumn planting is already documented (docs/garlic-autumn-plan.md) and is referenced, not recreated.

</domain>

<decisions>
## Implementation Decisions

### End-of-season ritual
- Celebration + goodbye framing, following the Phase 6 pattern ("tucking plants in", "say goodbye to each bed")
- Multi-day countdown (2-3 days), matching the Phase 6 pre-departure countdown structure:
  - **Day 1:** Final harvest celebration + garlic planting (bridge to Season 2 -- "we're putting something in the ground that will be here when we come back in spring")
  - **Day 2:** Plant removal + composting (child helps carry dead plants to compost pile)
  - **Day 3:** Bed covering with straw/mulch + reservoir draining + "see you next spring" goodbye
- Child actively participates in: final harvest party, spreading straw/mulch cover, carrying dead plants to compost pile
- Father-only tasks: reservoir draining, tool cleaning/storage, structural checks
- Garlic planting from docs/garlic-autumn-plan.md woven into Day 1 or 2 as a "looking forward" moment

### Season review format
- Crop-by-crop scorecard template with fields: crop name, planted date, germinated (Y/N), harvested (Y/N), yield (none/some/lots), child engagement (loved it / indifferent / avoided), verdict (keep/drop/try different variety)
- Child involvement: walk the beds together before cleanup, child points to "my favorite" and "didn't like" -- father records (simple, sensory, 5-minute activity)
- Dual format: markdown template in docs/ for human use + JSON schema in data/schemas/ for future data entry and comparison
- The child engagement column is the key differentiator -- it captures what matters for this project's core value

### Crop failure recovery
- Quick-swap replacement options WITH "it's OK, this happens" emotional framing for the child
- Replacement is presented as optional, not mandatory -- empty space is acceptable in a learning garden
- Added as a new section in the existing docs/troubleshooting-guide.md (keeps all problem-solving in one place)
- Month-by-month replanting windows (May through August) with specific replacement crop suggestions per month
- Includes new quick-grower suggestions not in the original plan (e.g., microgreens, quick radish succession) -- may require buying new seeds
- Covers common failure scenarios for OUR planted crops (seedling death, pest damage, disease) plus general replacements

### Soil refresh
- Full test-and-amend protocol, not just "add compost"
- Two-step timing: fall (add compost/mulch after cleanup, feeds soil over winter) + spring (top-dress and test before planting)
- Bed-specific guidance: Bed A reservoir zone (stays wetter, different amendment needs) vs Bed A standard zones vs Bed B (smaller, may deplete faster)
- Specific Danish products and suppliers named (consistent with Phase 1 shopping list approach)
- Optional soil test instructions included (pH, nutrients) with interpretation guide and amendment recommendations
- Builds on existing docs/soil-layers.md (original 3-layer recipe) as the baseline

### Perennial management
- Covers strawberry crowns, raspberry canes, and herb plants (what to cut, what to protect, when)
- Zone 7b / Danish maritime climate specific guidance
- Claude's discretion on format and level of detail

### Claude's Discretion
- Exact multi-day countdown task sequencing and timing
- Perennial management format and depth (standalone doc vs section in cleanup guide)
- Specific soil test kit recommendations for Danish market
- Which quick-grower crops to suggest as failure replacements
- Session script breaks and sensory transitions for the child
- How to integrate garlic planting into the countdown flow (Day 1 vs Day 2)

</decisions>

<specifics>
## Specific Ideas

- Garlic planting as a "looking forward" bridge: "We're putting these in the ground before winter. They'll sleep under the snow. Then in spring, green shoots will pop up." Creates continuity between seasons.
- Celebration + goodbye framing matches the established emotional patterns from Phase 6 (pre-departure countdown)
- Child picks favorites during bed walk -- simple sensory activity that generates the most valuable data point (what HE cared about)
- "It's OK, this happens" framing for crop failures -- the garden is for learning, not production. Failure is data, not disaster.
- Month-by-month recovery windows make the guidance useful in the moment of crisis, not just as reference reading

</specifics>

<code_context>
## Existing Code Insights

### Reusable Assets
- `docs/troubleshooting-guide.md`: Existing symptom-based guide with severity system -- SSN2-05 adds a crop failure recovery section to this file
- `docs/garlic-autumn-plan.md`: Complete garlic planting guide for October 2026 -- referenced in end-of-season ritual, not recreated
- `docs/soil-layers.md`: Original 3-layer soil recipe per bed type -- baseline for soil refresh documentation
- `docs/reservoir-build.md`: Reservoir construction details -- informs draining protocol for end-of-season cleanup
- `docs/reservoir-test-protocol.md`: Reservoir testing approach -- may inform seasonal draining/winterizing steps
- `data/schemas/`: Existing JSON schema pattern -- season review JSON schema extends this

### Established Patterns
- All deliverables are markdown files in `docs/` directory
- Session script format: step-by-step, timing, breaks, sensory transitions (Phases 2-3, 6)
- Celebration framing for milestone moments (pea harvest party, pre-departure harvest party)
- Phase 6 pre-departure countdown (3-day) as structural template for end-of-season countdown
- Shopping lists with specific Danish products, DKK prices, suppliers (Phase 1, 9)
- Dual format: markdown for humans + JSON for data system (Phase 4 pattern)

### Integration Points
- Troubleshooting guide: new section added (crop failure recovery)
- Garlic autumn plan: referenced from end-of-season ritual script
- Soil layers doc: soil refresh guide builds on and references original recipe
- Phase 4 data system: season review JSON schema extends existing schema patterns
- Weekly schedules (Phase 4): W44-W46 may need end-of-season tasks flagged

</code_context>

<deferred>
## Deferred Ideas

None -- discussion stayed within phase scope

</deferred>

---

*Phase: 11-season-2-preparation*
*Context gathered: 2026-03-28*
