# Phase 9: Operational Readiness - Research

**Researched:** 2026-03-28
**Domain:** Shopping list consolidation, purchase logistics, tool inventory, budget documentation
**Confidence:** HIGH

## Summary

Phase 9 is a documentation consolidation phase -- no new code, no new infrastructure. The project already has two shopping lists (`docs/shopping-list.md` for infrastructure and `docs/warm-season-shopping-list.md` for Phase 3 plants) but is missing a spring planting (Phase 2) shopping list. The father needs to walk into a garden center and know exactly what to buy for W16 planting day without re-reading five grid map files.

The gap analysis is straightforward: (1) Phase 2 plant purchases are described across five planting grid files and the planting day script but never consolidated into a single shopping list, (2) no purchase priority ordering exists across the three shopping lists, (3) tools are mentioned in passing across setup-guide.md and planting-day-script.md but never inventoried in one place, and (4) PROJECT.md still shows a budget constraint of "2,000-5,000 DKK" despite the infrastructure shopping list alone totaling ~9,825 DKK.

**Primary recommendation:** Create the missing spring planting shopping list, add cross-list purchase priority ordering, consolidate tool inventory, and update PROJECT.md budget -- all as markdown document edits, no data system changes.

<phase_requirements>
## Phase Requirements

| ID | Description | Research Support |
|----|-------------|-----------------|
| OPRD-01 | Spring planting shopping list covering all Phase 2 plant purchases (plugs, canes, herbs, seedlings) | Planting grids A-E and planting-day-script.md contain all Phase 2 plant types, varieties, and quantities -- needs consolidation into a single shopping list |
| OPRD-02 | Purchase priority ordering added to shopping lists (lead times, what to order first) | Three shopping lists exist (infrastructure, spring plants [new], warm-season); ordering depends on lead times (bare-root canes: order W14, seeds: anytime, seedlings: buy close to planting day) |
| OPRD-03 | Tool inventory section covering all required tools across build and planting days | Tools are scattered across setup-guide.md (drill, hose), planting-day-script.md (trowel, hand fork, watering cans), and slug-defense.md (rubbing alcohol). Needs consolidation. |
| OPRD-04 | PROJECT.md budget constraint updated to reflect actual ~10,000 DKK cost | PROJECT.md Context section shows "Budget: 2000-5000 DKK" and Constraints section shows "~10,000 DKK actual" -- these are contradictory. Infrastructure list alone is ~9,825 DKK Option A. |
</phase_requirements>

## Standard Stack

This phase is pure documentation -- markdown files only. No libraries, frameworks, or data system changes.

### Core
| Tool | Purpose | Why |
|------|---------|-----|
| Markdown | All deliverables are .md files in docs/ | Project convention per CLAUDE.md |
| Existing docs | Source data for consolidation | Grid maps, setup guide, planting scripts already contain all raw information |

### No New Dependencies
This phase creates no new file types, no JSON changes, no schema modifications. All outputs are markdown documents or edits to existing markdown.

## Architecture Patterns

### Existing Shopping List Pattern

The project already has two shopping lists with an established format. The spring planting list should follow the same conventions:

1. **Table format** with columns: Item, Qty, Variety, Where/Supplier, Approx DKK, Notes
2. **Category subtotals** in DKK with low/high range estimates
3. **Shopping timeline** section showing when to buy each category
4. **Practical notes** section with sourcing tips and fallback options
5. **Budget summary** table at the end

Source: `docs/shopping-list.md` (infrastructure) and `docs/warm-season-shopping-list.md` (Phase 3)

### Purchase Priority Pattern

Neither existing list has purchase priority ordering. This is a new cross-cutting concern that should be added as a section to each list OR as a standalone consolidated reference. Given the father needs a single "what to order when" view, a consolidated timeline across all three lists is most useful.

### Tool Inventory Pattern

The setup guide already has a "Before You Start Checklist" with some tool mentions. The planting day script has a prep section listing tools. These need merging into one reference.

## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| Plant quantity extraction | Manually counting from memory | Extract directly from planting grid files | Grid maps are the source of truth for what goes in each bed |
| Price estimation | Guessing DKK prices | Follow warm-season-shopping-list.md price format (~range) | Consistency with existing lists |
| Tool list | Inventing from scratch | Extract from setup-guide.md + planting-day-script.md + slug-defense.md | These docs already list every tool needed |

## Common Pitfalls

### Pitfall 1: Double-counting plants across phases
**What goes wrong:** A plant listed in the Phase 2 spring list also appears in the Phase 3 warm-season list.
**Why it happens:** Some plants (like calendula, borage, radish seeds) are sown in Phase 2 AND Phase 3, but seeds are bought once.
**How to avoid:** Cross-reference against warm-season-shopping-list.md. If a seed packet is already on the Phase 3 list, note "already purchased" rather than listing it again.
**Warning signs:** Total seed packet count exceeds what a person would actually buy.

### Pitfall 2: Missing the chive divisions sourcing question
**What goes wrong:** The chive divisions for Bed B are listed as "division" in the grid map but it's unclear if the family already has chives to divide or needs to buy plants.
**Why it happens:** Grid maps say "W16 -- division" which implies dividing existing clumps, but the family may not have chives.
**How to avoid:** List chive plants as "buy plant OR divide existing" with both options priced.

### Pitfall 3: Contradicting established shopping list prices
**What goes wrong:** The spring planting list uses different price ranges than the warm-season list for the same type of item (e.g., herb plants).
**Why it happens:** Inconsistent price research across lists.
**How to avoid:** Use the same price ranges already established in warm-season-shopping-list.md for equivalent items (herb plants 20-35 DKK, seedlings 25-40 DKK).

### Pitfall 4: Forgetting the pre-planting craft materials
**What goes wrong:** The planting day script references painted plant markers (wooden markers, acrylic paint, brushes) in a W15 pre-planting activity, but these never appear on any shopping list.
**Why it happens:** The craft activity is in the session script, not in the infrastructure or planting shopping lists.
**How to avoid:** Include plant marker craft materials in the spring planting shopping list or note them explicitly.

### Pitfall 5: Budget numbers not reconciled
**What goes wrong:** PROJECT.md gets updated with one number but the actual totals across three shopping lists add up to something different.
**Why it happens:** The infrastructure list has Option A (~9,825 DKK) and Option B (~9,225 DKK), plus spring plants (~TBD) and warm-season plants (~455-665 DKK).
**How to avoid:** Calculate the full budget as: infrastructure (Option A) + spring plants + warm-season plants + craft materials, and document the breakdown.

## Code Examples

### Phase 2 Spring Plant Inventory (extracted from grid maps)

These are ALL Phase 2 plant purchases extracted from the five planting grid files:

**Bed A (His Bed) -- W16:**
- 2x Strawberry Ostara plugs (everbearing)
- 1x Strawberry Korona plug (June-bearing)
- 1x Lamb's ear (Stachys) plant
- 3x Creeping thyme plants
- 1x Lemon balm plant
- 2x Viola seedlings
- 1 packet Calendula seeds (direct sow W17)
- 1 packet Pea shoot seeds (direct sow W16)
- 1 packet Radish seeds (succession from W18)

**Bed B (Raspberry) -- W16:**
- 3x Raspberry Autumn Bliss bare-root canes
- Chive divisions (12 clumps -- buy 2-3 plants to divide, OR divide existing)

**Bed C (Warm Crop / Pea & Cooking) -- W16:**
- 1 packet Pea seeds (Kelvedon Wonder) -- direct sow W16
- 1 packet Kale seeds (Nero di Toscana) -- direct sow W16-W17
- 1 packet Borage seeds -- direct sow W16-W17
- 1 packet Calendula seeds -- SAME packet as Bed A
- 1 packet Radish seeds -- SAME packet as Bed A

**Bed D (Salad & Herb Terrace) -- W16:**
- 1 packet Baby lettuce seed mix (cut-and-come-again)
- 1 packet Spring onion seeds (White Lisbon)
- 2x Creeping thyme plants (in addition to Bed A's 3)
- 2x Viola seedlings (in addition to Bed A's 2)

**Bed E (Future Warm Terrace) -- W16:**
- 1 packet Borage seeds -- SAME packet as Bed C
- 1 packet Radish seeds -- SAME packet as Bed A/C
- 1 packet Calendula seeds -- SAME packet as Bed A/C

**De-duplicated seed packet count:**
- Pea seeds (Kelvedon Wonder): 1 packet
- Pea shoot seeds: 1 packet (or same as pea seeds if using same variety)
- Kale seeds (Nero di Toscana): 1 packet
- Radish seeds: 1 packet (used across Beds A, C, E)
- Calendula seeds: 1 packet (used across Beds A, C, E)
- Borage seeds: 1 packet (used across Beds C, E)
- Baby lettuce seed mix: 1 packet
- Spring onion seeds (White Lisbon): 1 packet

**De-duplicated plant/seedling count:**
- 3x Strawberry plugs (2 Ostara + 1 Korona)
- 3x Raspberry Autumn Bliss bare-root canes
- 1x Lamb's ear plant
- 5x Creeping thyme plants (3 for Bed A + 2 for Bed D)
- 1x Lemon balm plant
- 4x Viola seedlings (2 for Bed A + 2 for Bed D)
- 2-3x Chive plants (to divide into 12 clumps for Bed B perimeter)

### Tool Inventory (extracted from existing docs)

**From setup-guide.md (build day):**
- Drill with 10-12mm bit (reservoir PVC holes)
- Hose with water tap connection
- Scissors or tin snips (cutting hardware cloth/mesh)

**From planting-day-script.md (planting day):**
- Trowel
- Hand fork
- Small watering can (child-sized)
- Large watering can (adult)
- Phone/camera (milestone photo)

**From slug-defense.md:**
- Rubbing alcohol / isopropyl (cleaning steel before copper tape)

**From planting-day-script.md (pre-planting craft):**
- 8-12 wooden plant markers
- Acrylic paint set
- 2-3 brushes
- Newspaper/tablecloth

**From warm-season-shopping-list.md (Phase 3 additions):**
- Ruler stake (2m+ wood lath, marked in 10cm increments)
- Tomato stake or cage (1.5m+)
- Twine/soft ties

**Potentially needed but not explicitly listed:**
- Gloves (gardening)
- Wheelbarrow or large bucket (carrying soil, especially upstairs to terrace)
- Measuring tape (verifying spacing)
- Waterproof marker (for ruler stake)
- Dibber or thick stick (for leek planting holes, Phase 3)

### Budget Reconciliation

| Category | Low Estimate (DKK) | High Estimate (DKK) | Source |
|----------|--------------------|--------------------|--------|
| Infrastructure (Option A) | 9,100 | 10,300 | shopping-list.md |
| Spring plants (Phase 2) | ~400 | ~700 | To be calculated |
| Warm-season plants (Phase 3) | 455 | 665 | warm-season-shopping-list.md |
| Craft materials (markers/paint) | 50 | 150 | planting-day-script.md |
| **Total** | **~10,005** | **~11,815** | |

PROJECT.md currently says "Budget: 2000-5000 DKK" in the Context section and "~10,000 DKK actual" in the Constraints section. Both need to reflect the real total.

## State of the Art

Not applicable -- this is a documentation consolidation phase, not a technology decision phase.

## Open Questions

1. **Chive sourcing: divide or buy?**
   - What we know: Bed B needs 12 chive clumps. Grid says "division" implying splitting existing plants.
   - What's unclear: Does the family have existing chive plants to divide?
   - Recommendation: List "2-3 chive plants (to divide)" as a purchase item with a note "skip if you already have chives to divide."

2. **Pea shoots vs pea seeds: same packet?**
   - What we know: Bed A uses "pea shoot seeds" and Bed C uses "Kelvedon Wonder pea seeds."
   - What's unclear: Are pea shoots a different variety or the same Kelvedon Wonder?
   - Recommendation: List as 1 packet Kelvedon Wonder (used for both pea shoots and climbing peas). Pea shoots are just peas harvested young.

3. **Lemon balm containment pot**
   - What we know: Grid map says "Plant in a bottomless 20cm terracotta pot sunk into the soil."
   - What's unclear: Whether this pot needs to be on the shopping list or if any household container works.
   - Recommendation: Add "1x 20cm terracotta pot (for lemon balm containment)" to spring list with note that any old pot with bottom knocked out works.

4. **Danish supplier specifics for bare-root canes and strawberry plugs**
   - What we know: Warm-season list says "garden center" for seedlings.
   - What's unclear: Lead times for bare-root raspberry canes and strawberry plugs in Denmark. These may need to be ordered online 2-4 weeks ahead.
   - Recommendation: Research whether Danish garden centers (Plantorama, Bilka Garden) stock Autumn Bliss and Ostara/Korona in W14-W16, or if online ordering (e.g., blomsterlandet.dk, plantetorvet.dk) is needed.

## Validation Architecture

### Test Framework
| Property | Value |
|----------|-------|
| Framework | Manual verification (documentation phase) |
| Config file | none |
| Quick run command | Visual inspection of shopping list completeness |
| Full suite command | Cross-reference all grid maps against shopping list entries |

### Phase Requirements to Test Map
| Req ID | Behavior | Test Type | Automated Command | File Exists? |
|--------|----------|-----------|-------------------|-------------|
| OPRD-01 | Spring shopping list has all Phase 2 plants | manual-only | Compare grid map plant lists against shopping list rows | N/A -- doc review |
| OPRD-02 | Purchase priority ordering exists | manual-only | Verify timeline section covers all three shopping lists | N/A -- doc review |
| OPRD-03 | Tool inventory is complete | manual-only | Cross-reference setup-guide + planting-day-script + slug-defense against tool list | N/A -- doc review |
| OPRD-04 | PROJECT.md budget updated | manual-only | Check PROJECT.md Constraints section for ~10,000+ DKK figure with rationale | N/A -- doc review |

### Sampling Rate
- **Per task commit:** Visual review of changed files
- **Per wave merge:** Cross-reference grid maps against shopping lists for completeness
- **Phase gate:** All four OPRD requirements verified by inspection

### Wave 0 Gaps
None -- this is a documentation phase with no test infrastructure needed.

## Sources

### Primary (HIGH confidence)
- `docs/shopping-list.md` -- existing infrastructure shopping list with established format
- `docs/warm-season-shopping-list.md` -- existing Phase 3 shopping list with plant pricing
- `docs/planting-grid-bed-a.md` through `docs/planting-grid-bed-e.md` -- source of truth for all plant types, varieties, quantities, and positions
- `docs/planting-day-script.md` -- tool list and craft materials for planting sessions
- `docs/setup-guide.md` -- build day tool requirements and sequence
- `.planning/PROJECT.md` -- current budget figures needing update

## Metadata

**Confidence breakdown:**
- Plant inventory extraction: HIGH -- grid maps are definitive and complete
- Tool inventory: HIGH -- setup guide and planting scripts list all tools explicitly
- Budget reconciliation: HIGH -- all three shopping lists have specific DKK figures
- Purchase priority/lead times: MEDIUM -- lead times for Danish nursery stock (bare-root canes, strawberry plugs) need verification at order time

**Research date:** 2026-03-28
**Valid until:** 2026-04-13 (W16 planting day deadline -- this phase must complete before then)
