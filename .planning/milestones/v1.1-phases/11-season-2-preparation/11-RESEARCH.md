# Phase 11: Season 2 Preparation - Research

**Researched:** 2026-03-28
**Domain:** End-of-season garden management, perennial care, soil refresh, season review, crop failure recovery
**Confidence:** HIGH

## Summary

Phase 11 produces documentation for everything that happens after the growing season ends (W44-W46) and a mid-season crop failure recovery guide. The deliverables are all markdown documents in `docs/` plus one JSON schema in `data/schemas/`. No code, no infrastructure, no data migration -- purely documentation work building on established project patterns.

The domain knowledge is well-understood: raised bed winterization, perennial care for strawberries/raspberries/herbs, soil amendment cycles, and quick-growing replacement crops are thoroughly documented across extension services and gardening authorities. The project-specific constraints (2 beds, Zone 7b Danish maritime climate, ADHD/Autism-adapted sessions, corten steel beds on grass) narrow the research to specific, actionable guidance.

**Primary recommendation:** Follow the established session script pattern (from Phases 2-3 and 6) for the end-of-season countdown, and keep all other deliverables as straightforward reference documents in `docs/`. The crop failure recovery section integrates into the existing `docs/troubleshooting-guide.md`.

<user_constraints>
## User Constraints (from CONTEXT.md)

### Locked Decisions
- End-of-season ritual: Multi-day countdown (2-3 days) with celebration + goodbye framing, matching Phase 6 pre-departure countdown structure. Day 1: Final harvest + garlic planting. Day 2: Plant removal + composting. Day 3: Bed covering with straw/mulch + reservoir draining + goodbye.
- Child actively participates in: final harvest party, spreading straw/mulch cover, carrying dead plants to compost pile. Father-only: reservoir draining, tool cleaning/storage, structural checks.
- Garlic planting from docs/garlic-autumn-plan.md woven into Day 1 or 2.
- Season review: Crop-by-crop scorecard template with fields (crop name, planted date, germinated Y/N, harvested Y/N, yield none/some/lots, child engagement loved/indifferent/avoided, verdict keep/drop/try different). Dual format: markdown template + JSON schema. Child involvement: 5-minute bed walk picking "my favorite" and "didn't like."
- Crop failure recovery: Added as new section in existing docs/troubleshooting-guide.md. Quick-swap replacements WITH emotional framing. Replacement is optional. Month-by-month replanting windows (May-August). Includes quick-growers not in original plan (microgreens, quick radish succession). Covers common failure scenarios for planted crops.
- Soil refresh: Full test-and-amend protocol. Two-step timing (fall add compost/mulch + spring top-dress and test). Bed-specific guidance (Bed A reservoir zone vs standard zones vs Bed B). Danish products and suppliers named. Optional soil test instructions.
- Perennial management: Covers strawberry crowns, raspberry canes, and herb plants. Zone 7b / Danish maritime climate specific.

### Claude's Discretion
- Exact multi-day countdown task sequencing and timing
- Perennial management format and depth (standalone doc vs section in cleanup guide)
- Specific soil test kit recommendations for Danish market
- Which quick-grower crops to suggest as failure replacements
- Session script breaks and sensory transitions for the child
- How to integrate garlic planting into the countdown flow (Day 1 vs Day 2)

### Deferred Ideas (OUT OF SCOPE)
None -- discussion stayed within phase scope.
</user_constraints>

<phase_requirements>
## Phase Requirements

| ID | Description | Research Support |
|----|-------------|-----------------|
| SSN2-01 | End-of-season cleanup guide (W44-W46) covering plant removal, composting, reservoir draining | End-of-season countdown script pattern, reservoir winterization procedure, raised bed cleanup best practices |
| SSN2-02 | Perennial management notes for strawberry crowns, raspberry canes, and herb plants | Zone 7b overwintering research for each perennial type, pruning timing, mulch protection depths |
| SSN2-03 | Year 2 soil refresh documentation (when and how to amend raised bed soil) | Two-step fall/spring amendment protocol, volume calculations, bed-specific guidance for reservoir zone |
| SSN2-04 | Season review template for capturing lessons learned | Crop scorecard fields, JSON schema pattern from existing data/schemas/, dual-format approach |
| SSN2-05 | Crop failure recovery section added to troubleshooting guide with mid-season replanting windows | Month-by-month replacement windows for Danish climate, quick-growing crop options, emotional framing pattern |
</phase_requirements>

## Architecture Patterns

### Recommended Deliverable Structure

```
docs/
  end-of-season-guide.md          # SSN2-01: Cleanup + countdown script (new)
  perennial-care.md               # SSN2-02: Perennial management (new)
  soil-refresh-guide.md           # SSN2-03: Year 2 soil amendment (new)
  season-review-template.md       # SSN2-04: Crop scorecard template (new)
  troubleshooting-guide.md        # SSN2-05: Add crop failure recovery section (existing, extend)
data/
  schemas/
    season-review.schema.json     # SSN2-04: JSON schema for season review data (new)
```

### Pattern 1: Session Script (End-of-Season Countdown)

**What:** Multi-day countdown script matching the Phase 6 vacation-countdown-script.md pattern.
**When to use:** SSN2-01 end-of-season guide.
**Structure from Phase 6 template:**
- Motor Skill Split table (child tasks vs father tasks)
- Day-by-day sections with duration targets, prep checklists, timed steps, breaks, transitions
- Done Signal per day with verification checklist
- Meltdown Protocol and Weather Abort sections
- Cross-References section

The existing `docs/vacation-countdown-script.md` is the structural template. The end-of-season countdown uses the same format but with 2-3 days instead of 3.

### Pattern 2: Reference Document (Perennial Care, Soil Refresh)

**What:** Standalone reference docs with actionable guidance organized by topic.
**When to use:** SSN2-02 and SSN2-03.
**Structure:** Similar to existing docs like `soil-layers.md` and `reservoir-build.md` -- clear headings, step-by-step instructions, timing tables, material lists, cross-references.

### Pattern 3: Troubleshooting Guide Extension

**What:** New section added to the existing `docs/troubleshooting-guide.md`.
**When to use:** SSN2-05 crop failure recovery.
**Structure:** Must match existing severity system (green/yellow/red circles), symptom-based format, "Child action" prompts, photo placeholders, and bed-specific references.

### Pattern 4: Dual-Format Template (Season Review)

**What:** Markdown template for human use + JSON schema for data entry.
**When to use:** SSN2-04.
**Structure:** Follows the Phase 4 dual-format pattern. Markdown template in `docs/`, JSON schema in `data/schemas/` following existing schema conventions (see `crop.schema.json` for style).

### Anti-Patterns to Avoid
- **Duplicating garlic content:** The garlic planting guide already exists at `docs/garlic-autumn-plan.md`. The end-of-season script should reference it, not recreate it.
- **Over-engineering the JSON schema:** Keep the season review schema simple -- it captures one season of data, not a multi-year database.
- **Generic Zone 7 advice:** All guidance must be specific to the Haven garden's actual beds, crops, and setup. Reference Bed A/B by name, mention specific crops planted.

## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| End-of-season script | New format | Copy Phase 6 vacation-countdown-script.md structure | Established pattern with motor skill split, meltdown protocol, breaks |
| Crop scorecard fields | Custom fields | Use the fields locked in CONTEXT.md | User decided exact fields during context discussion |
| Troubleshooting format | New style | Match existing troubleshooting-guide.md format exactly | Consistency -- severity system, child actions, photo placeholders |
| JSON schema style | New conventions | Follow crop.schema.json patterns | Existing schemas use consistent conventions (bilingual labels, enums, required fields) |

## Common Pitfalls

### Pitfall 1: Reservoir Winterization Incomplete
**What goes wrong:** Standing water in the PVC reservoir freezes, expands, and cracks pipes or breaks joints.
**Why it happens:** The reservoir is below the soil surface and easy to forget during cleanup.
**How to avoid:** The end-of-season guide must include explicit reservoir draining steps. The existing `docs/reservoir-build.md` already mentions this: "In autumn, let the reservoir drain naturally. Do not leave standing water over winter -- freezing could damage PVC pipes. If possible, tip the bed slightly or remove the overflow stub to drain fully."
**Warning signs:** Water still visible at overflow in November.

### Pitfall 2: Strawberry Crowns Killed by Freeze
**What goes wrong:** Unprotected strawberry crowns die at -9C (15F), which is possible in Danish winters.
**Why it happens:** Raised beds expose crowns to colder temperatures than ground-level planting because the soil mass is smaller and freezes faster.
**How to avoid:** Apply 10-15cm straw mulch after 2-3 hard frosts in autumn (typically late October/November in Vejle). Do not mulch too early -- the crowns need to harden off first.
**Warning signs:** Crowns exposed above soil surface, no mulch by mid-November.

### Pitfall 3: Autumn Bliss Raspberry Pruning at Wrong Time
**What goes wrong:** Pruning in autumn removes next year's fruiting wood (if summer-fruiting) or leaves dead canes standing all winter.
**Why it happens:** Confusion between summer-fruiting and autumn-fruiting raspberry pruning. Autumn Bliss is a primocane (autumn-fruiting) variety.
**How to avoid:** Autumn Bliss fruits on current-year canes. Prune ALL canes to ground level in February, not in autumn. In autumn, just remove any dead or diseased canes and leave the rest standing until late winter.
**Warning signs:** Pruning in October/November instead of February.

### Pitfall 4: Soil Level Drop Surprise in Year 2
**What goes wrong:** The garden waste middle layer decomposes over the season, causing soil level to drop 5-10cm. Year 2 starts with beds that look under-filled.
**Why it happens:** This is expected (documented in soil-layers.md) but can be alarming if not planned for.
**How to avoid:** The soil refresh guide must explicitly state that 5-10cm settling is normal and the spring top-dress compensates for it.
**Warning signs:** Visible gap between soil surface and bed rim in spring.

### Pitfall 5: Crop Failure Recovery Written as Academic Reference
**What goes wrong:** The crop failure section reads like a gardening encyclopedia instead of crisis-moment guidance.
**Why it happens:** Writing for "information" instead of "action in a stressful moment."
**How to avoid:** Use the month-by-month format locked in CONTEXT.md. Write for a parent whose child's plant just died -- start with emotional framing ("It's OK, this happens"), then give 2-3 specific replacement options with sowing instructions. Keep each failure scenario to half a page max.
**Warning signs:** More than 3 paragraphs before the first actionable step.

## Domain Knowledge

### End-of-Season Cleanup (W44-W46, late October - mid November)

**Plant removal sequence:**
1. Remove all annual crops (tomatoes, cucumbers, peppers, beans, basil, lettuce, radish, spring onions, broccoli, calendula, nasturtium, sunflowers, borage, dill, viola, peas)
2. Cut back but DO NOT remove perennials: strawberry crowns (trim dead leaves, leave crown), raspberry canes (leave standing until February), thyme (light trim only), chives (cut to 5cm), lemon balm (cut to 15cm)
3. Compost healthy plant material. Discard diseased material in household waste (not compost)

**Composting guidance:** The project does not currently have a dedicated compost setup. The CONTEXT.md mentions "carry dead plants to compost pile" -- the guide should note that a simple compost pile or bin is needed. If none exists, bagged garden waste for municipal collection is the fallback.

**Reservoir draining (Bed A north zone only):**
- Remove overflow stub or open overflow to let water drain
- Pour water through fill tube and listen -- if splashing, reservoir still has water
- Let drain naturally over several days
- Once drained, optionally plug overflow loosely to prevent debris entry
- Source: reservoir-build.md end-of-season note

**Tool storage:** Clean, dry, and store tools. Check trellis for damage, store any removable parts. Corten steel beds require no maintenance (they are designed to weather).

### Perennial Management (Zone 7b, Danish Maritime Climate)

**Strawberry crowns (Ostara + Korona in Bed B):**
- After final harvest (September for Ostara everbearing), trim dead and diseased leaves but leave crown and healthy low growth
- Do NOT mow/cut to ground in first year -- plants are still establishing
- After 2-3 hard frosts (late October/November in Vejle), apply 10-15cm straw mulch over the crowns
- In spring, rake straw aside when new growth appears (typically March/April) but leave some around base as summer mulch
- Year 2: thin runners, remove weak plants, keep strongest crowns at 15cm spacing
- Raised beds freeze faster than ground -- extra mulch is important
- Confidence: HIGH (multiple extension service sources agree)

**Raspberry Autumn Bliss (3 canes in Bed A south zone):**
- Autumn-fruiting (primocane) variety -- fruits on current-year wood
- In autumn (after last harvest, typically October): remove any dead/diseased canes only
- In February: cut ALL canes to ground level (5-10cm stubs). New canes grow from the base in spring
- Apply 5-8cm compost or well-rotted manure mulch around the base after February pruning
- Do NOT prune in autumn/November -- the standing canes provide some frost protection to the roots
- First year (2026) is establishment year -- expect small harvest. Full production begins Year 2
- Confidence: HIGH (RHS, Thompson & Morgan, multiple sources agree on primocane pruning)

**Herbs:**
- **Thyme** (Bed A middle, Bed B edges): Hardy perennial. Leave in place over winter. Do NOT prune in autumn. Light trim after flowering in summer only. Good drainage in raised beds helps survival. Mulch lightly (2-3cm) if severe cold expected.
- **Chives** (Bed A south zone): Very hardy. Foliage dies back naturally. Cut to 5cm in late autumn. Bulbs survive to -20F with mulch. Will regrow vigorously in spring.
- **Lemon balm** (Bed B, in sunken pot): Hardy. Cut back to 15cm in autumn. The pot provides good drainage. Mulch top of pot with 5cm straw.
- **Mint** (pot beside Bed B): Hardy. Cut to ground level in autumn. Pot may need wrapping with bubble wrap or moving against house wall in severe cold (pots freeze faster than beds).
- Confidence: HIGH (NC State Extension, multiple perennial herb guides)

**Lamb's ear (Bed B):** Semi-evergreen perennial. Remove dead or mushy leaves in autumn. Leave rosettes intact. Hardy in Zone 7b. No special winter protection needed.

### Soil Refresh Protocol

**Fall amendment (W44-W46, after cleanup):**
1. After removing spent crops, rake bed surface smooth
2. Add 2-5cm layer of compost or well-rotted garden compost over entire bed surface
3. Cover with 5-10cm straw mulch for winter protection
4. The compost feeds soil organisms over winter, improving structure for spring

**Spring amendment (W14-W15, before planting):**
1. Remove or rake aside winter mulch
2. Check soil level -- expect 5-10cm drop from Year 1 due to garden waste layer decomposition
3. Top-dress with 5-10cm fresh hojbedsmuld to restore level to bed rim
4. Optional: soil test before planting (pH, N-P-K)
5. For heavy feeders (tomato, cucumber, pepper zone): mix in additional compost or slow-release fertilizer

**Bed-specific considerations:**
- **Bed A north zone (reservoir):** Soil stays wetter due to sub-irrigation. May compact more. Check reservoir pipes are intact after winter. Amendment sits on top of geotextile/gravel system -- no different than standard zone for top-dressing.
- **Bed A middle/south zones:** Standard top-dress. Raspberry zone (south) gets extra compost around canes in February after pruning.
- **Bed B (smaller volume):** 360 liters total. Smaller soil mass = depletes faster = may need slightly more aggressive top-dressing (up to 10cm). Monitor soil quality more closely.

**Danish products for soil refresh:**
- **Hojbedsmuld:** The same raised bed soil mix used in Year 1. Available at Plantorama, Bauhaus garden section, and online Danish garden suppliers. This is the primary top-dress material.
- **Kompost (compost):** Available bagged at Danish garden centers or homemade. "Havekompost" or "plante kompost" at Plantorama/Bauhaus.
- **Slow-release fertilizer:** NPK-based granular fertilizer (e.g., "havegodning" or "langtidsgodning") for heavy feeder zones.
- **Soil test kits:** Simple pH test kits available at most garden centers (30-50 DKK). For full nutrient analysis, Danish labs offer postal soil testing (e.g., Eurofins Miljoe).
- Confidence: MEDIUM (product names based on standard Danish garden center inventory; specific availability should be verified at time of purchase)

### Crop Failure Recovery (Quick-Growing Replacements)

**Month-by-month replanting windows for Danish Zone 7b:**

| Month | Window | Good Replacements | Days to Harvest |
|-------|--------|-------------------|-----------------|
| May | After last frost (~May 15) | Radish, baby lettuce, arugula, basil (seedling) | 20-30 days |
| June | Full growing season | Radish, baby lettuce, bush beans, quick basil, cilantro | 20-45 days |
| July | Mid-season, still warm | Radish, baby lettuce, arugula, quick spinach, cilantro, microgreens (indoor) | 20-40 days |
| August | Last window for outdoor | Radish, baby lettuce, arugula, spinach, kale (for autumn harvest) | 25-50 days |

**Quick-grower options not in original plan:**
- **Microgreens** (indoor, any time): Harvest in 7-14 days. Grow on a tray indoors on a windowsill. Sunflower, radish, and pea microgreens are easy and engaging for a child. Not technically garden growing but excellent for crisis recovery -- "We can grow something right now!"
- **Arugula/rocket (rucola):** 21 days to baby leaf. Direct sow. Peppery taste, fast visual results.
- **Quick radish succession:** Cherry Belle or French Breakfast varieties, 21-25 days seed to harvest. Can fill any gap.
- **Cilantro (koriander):** 21-30 days to first cutting. Direct sow May-July.

**Common failure scenarios for planted crops:**
1. Seedling death (damping off, slug damage, frost damage) -- most common in W16-W20
2. Pest damage (caterpillars on broccoli, aphid overwhelming, slug devastation)
3. Disease (powdery mildew on cucumber, blight on tomato, botrytis on strawberry)
4. Environmental stress (heat bolt on lettuce, cold damage on warm crops planted too early)

### Season Review Template Fields

**Crop scorecard (locked fields from CONTEXT.md):**
- Crop name (from data/crops/*.json id)
- Planted date (ISO week)
- Germinated (yes/no)
- Harvested (yes/no)
- Yield (none/some/lots)
- Child engagement (loved it / indifferent / avoided)
- Verdict (keep / drop / try different variety)
- Notes (free text)

**JSON schema should follow existing patterns:**
- Use `$schema` and `$id` fields
- Bilingual labels (en/da) where appropriate
- Enum values for constrained fields
- Required vs optional fields clearly marked
- Reference crop IDs from existing crop data files

## Code Examples

### Season Review JSON Schema Structure
```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "season-review.schema.json",
  "title": "Haven Season Review",
  "type": "object",
  "required": ["season", "year", "crops", "summary"],
  "properties": {
    "season": { "type": "integer" },
    "year": { "type": "integer" },
    "crops": {
      "type": "array",
      "items": {
        "type": "object",
        "required": ["crop_id", "planted_week", "germinated", "harvested", "yield", "child_engagement", "verdict"],
        "properties": {
          "crop_id": { "type": "string", "description": "Matches id from data/crops/*.json" },
          "planted_week": { "type": "string", "pattern": "^W[0-9]{2}$" },
          "germinated": { "type": "boolean" },
          "harvested": { "type": "boolean" },
          "yield": { "type": "string", "enum": ["none", "some", "lots"] },
          "child_engagement": { "type": "string", "enum": ["loved_it", "indifferent", "avoided"] },
          "verdict": { "type": "string", "enum": ["keep", "drop", "try_different_variety"] },
          "notes": { "type": "string" }
        }
      }
    },
    "summary": {
      "type": "object",
      "properties": {
        "favorite_crop": { "type": "string" },
        "least_favorite_crop": { "type": "string" },
        "biggest_success": { "type": "string" },
        "biggest_challenge": { "type": "string" },
        "changes_for_next_year": { "type": "array", "items": { "type": "string" } }
      }
    }
  }
}
```
Source: Extrapolated from existing `data/schemas/crop.schema.json` conventions.

### Troubleshooting Guide Extension Pattern
```markdown
## Crop Failure Recovery

> **"It's OK -- this happens to every garden."** Plants fail sometimes. It does not mean you did anything wrong. An empty spot in the bed is an opportunity, not a problem. You can replant, or you can leave it -- both are fine.

### A seedling died -- what can I plant instead?

**Severity:** :green_circle: No rush

**What happened:** [scenario description]

**What to do:**
1. [Emotional framing first]
2. [Check the month -- what can go in now?]
3. [Specific replacement options]

**Child action:** "[age-appropriate prompt]"
```
Source: Pattern matching existing troubleshooting-guide.md format.

## Validation Architecture

### Test Framework
| Property | Value |
|----------|-------|
| Framework | Manual review (documentation project, no executable code) |
| Config file | none |
| Quick run command | `ls docs/end-of-season-guide.md docs/perennial-care.md docs/soil-refresh-guide.md docs/season-review-template.md data/schemas/season-review.schema.json` |
| Full suite command | Manual review: verify all 5 deliverables exist and cross-references resolve |

### Phase Requirements to Test Map
| Req ID | Behavior | Test Type | Automated Command | File Exists? |
|--------|----------|-----------|-------------------|-------------|
| SSN2-01 | End-of-season cleanup guide exists with W44-W46 tasks | smoke | `test -f docs/end-of-season-guide.md && grep -q "reservoir" docs/end-of-season-guide.md` | Wave 0 |
| SSN2-02 | Perennial management notes exist | smoke | `test -f docs/perennial-care.md && grep -q "strawberry" docs/perennial-care.md` | Wave 0 |
| SSN2-03 | Soil refresh documentation exists | smoke | `test -f docs/soil-refresh-guide.md && grep -q "hojbedsmuld" docs/soil-refresh-guide.md` | Wave 0 |
| SSN2-04 | Season review template exists in both formats | smoke | `test -f docs/season-review-template.md && test -f data/schemas/season-review.schema.json` | Wave 0 |
| SSN2-05 | Crop failure recovery section in troubleshooting guide | smoke | `grep -q "Crop Failure" docs/troubleshooting-guide.md` | Wave 0 |

### Sampling Rate
- **Per task commit:** `ls -la` on expected output files
- **Per wave merge:** Manual review of all deliverables + cross-reference check
- **Phase gate:** All 5 deliverables exist, troubleshooting guide extended, JSON schema valid

### Wave 0 Gaps
None -- this is a documentation-only phase. No test infrastructure needed beyond file existence checks. All validation is smoke-level (file exists, key terms present).

## Sources

### Primary (HIGH confidence)
- Existing project docs: `docs/vacation-countdown-script.md` (session script pattern), `docs/troubleshooting-guide.md` (extension target), `docs/soil-layers.md` (baseline), `docs/reservoir-build.md` (winterization note), `docs/garlic-autumn-plan.md` (cross-reference)
- Existing schemas: `data/schemas/crop.schema.json` (JSON schema conventions)

### Secondary (MEDIUM confidence)
- [UMN Extension: Growing Strawberries](https://extension.umn.edu/fruit/growing-strawberries-home-garden) - strawberry winter care, mulching, perennial management
- [Epic Gardening: Overwinter Strawberries](https://www.epicgardening.com/overwinter-strawberries/) - 6-step overwintering guide
- [RHS: Raspberry Autumn Bliss](https://www.rhs.org.uk/plants/76281/rubus-idaeus-autumn-bliss-(f)/details) - primocane pruning guidance
- [Thompson & Morgan: Pruning Autumn Raspberries](https://www.thompson-morgan.com/pruning/raspberries) - February ground-level pruning
- [NC State Extension: Winterizing the Herb Garden](https://content.ces.ncsu.edu/winterizing-the-herb-garden) - herb overwintering by type
- [Illinois Extension: Refreshing Raised Bed Soil](https://extension.illinois.edu/news-releases/refreshing-raised-bed-soil-generates-exceptional-results) - year 2 soil amendment
- [Gardener's Supply: Recharge Raised Bed Soil](https://www.gardeners.com/blogs/raised-bed-articles/recharge-your-raised-bed-9627) - compost top-dressing protocol
- [Savvy Gardening: Preparing Raised Beds for Winter](https://savvygardening.com/preparing-raised-beds-for-winter/) - autumn cleanup checklist
- [UMN Extension: Midsummer Planting for Fall Harvest](https://extension.umn.edu/planting-and-growing-guides/planting-vegetables-midsummer-fall-harvest) - replacement crop timing

### Tertiary (LOW confidence)
- Danish product names (hojbedsmuld, havekompost, langtidsgodning) -- based on general knowledge of Danish garden center inventory. Specific product availability should be verified at Plantorama/Bauhaus at time of purchase.
- Eurofins Miljoe soil testing service -- known Danish lab but postal testing service details should be confirmed.

## Metadata

**Confidence breakdown:**
- End-of-season cleanup: HIGH - well-established practices, project-specific reservoir draining already documented
- Perennial management: HIGH - multiple authoritative extension service sources, primocane pruning is unambiguous
- Soil refresh: HIGH for protocol, MEDIUM for Danish product specifics
- Season review template: HIGH - fields locked by user, JSON schema follows existing project conventions
- Crop failure recovery: HIGH for replacement crop options, MEDIUM for exact Danish growing windows (first frost variability)

**Research date:** 2026-03-28
**Valid until:** 2026-10-31 (valid through the end-of-season execution window)
