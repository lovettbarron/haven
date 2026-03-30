# Haven -- A Learning Garden

## What This Is

A backyard garden project in Vejle, Denmark designed as a developmental tool for a 7-year-old with ADHD and Autism. Two corten steel raised beds give him incrementally increasing agency over something living -- his own beds, his own daily routine, his own harvest decisions. The project delivers complete physical garden plans, ADHD-adapted session scripts, structured JSON data for Home Assistant integration, and comprehensive documentation for family, neighbors, and season transitions. All planning and documentation is complete through v1.1; the garden is ready for physical execution starting W16.

## Core Value

A child who independently checks on, cares for, and harvests from plants he chose to grow -- and sees the direct connection between his effort and the food on his plate.

## Requirements

### Validated

- ✓ Raised bed specifications with soil layer breakdown — v1.0
- ✓ Shopping/materials list with corten steel and budget alternatives — v1.0
- ✓ Setup instructions for bed construction and soil filling — v1.0
- ✓ Property-specific raised bed placement recommendations — v1.0
- ✓ Property visualization with bed placement, sun patterns, orientation — v1.0
- ✓ Denmark-appropriate crop recommendations — v1.0
- ✓ Bed-by-bed planting distribution with companion planting — v1.0
- ✓ Week-by-week maintenance and growth plan (W15-W44) — v1.0
- ✓ Staggered planting schedule for continuous harvest — v1.0
- ✓ Structured JSON data format for all 27 crops — v1.0
- ✓ Home Assistant sensor recommendations and entity schemas — v1.0
- ✓ Troubleshooting guide (symptom-based, father-son reference) — v1.0
- ✓ Difficulty-tiered crop collection — v1.0
- ✓ Neighbor vacation guide — v1.0
- ✓ CLAUDE.md project file for AI continuity — v1.0
- ✓ Self-watering reservoirs and vacation preparation — v1.0
- ✓ Canonical bed identity (A-E) across all documents and data — v1.1
- ✓ Daily routine card and weekly garden walk (child-facing, printable) — v1.1
- ✓ Between-session engagement activities (treasure hunts, photo log) — v1.1
- ✓ Spring planting shopping list with purchase priority timeline — v1.1
- ✓ Tool inventory for build day and planting days — v1.1
- ✓ Home Assistant setup walkthrough with copy-paste YAML — v1.1
- ✓ End-of-season cleanup guide and perennial care reference — v1.1
- ✓ Soil refresh protocol and season review template — v1.1
- ✓ Crop failure recovery with mid-season replanting windows — v1.1
- ✓ Planning artifact accuracy and traceability — v1.1

### Active

- [ ] Garlic hardneck cloves planted October 2026 (COOK-02, docs ready, awaiting physical planting)
- [ ] v2 IoT sensor deployment (Zigbee soil moisture/temperature per bed)
- [ ] v2 season 2 crops (carrots, fennel, seed saving, exotic varieties)

### Out of Scope

- Greenhouse or polytunnel — raised beds are sufficient
- Automated irrigation — manual watering is the agency-building routine (reservoirs OK for vacation)
- Indoor seed starting — direct sow or buy seedlings
- Fruit trees — consider after first season validates approach
- Lemon/citrus outdoors — not viable in Danish climate (zone 7b)
- Exotic fruits (pomegranate, passion fruit, kiwi) — climate incompatible
- Corn/sweetcorn — needs huge space, unreliable ripening in Danish raised beds
- Melon/watermelon — needs sustained heat Denmark rarely provides
- Courgette as main crop — takes enormous space, powdery mildew in Danish humidity
- Brussels sprouts — 150+ days, zero engagement value

## Context

### Current State (post v1.1)
- **LOC:** ~6,900 lines markdown documentation, ~8,900 lines JSON data
- **Files:** 22 docs in docs/, 68 data files in data/, comprehensive .planning/ archive
- **Tech stack:** Markdown docs, JSON crop/schedule/sensor data, Home Assistant YAML
- **Milestones shipped:** v1.0 Foundation Season (Phases 1-6), v1.1 Gap Closure (Phases 7-12)
- **Requirements:** 88 total (59 v1.0 + 29 v1.1), all satisfied except COOK-02 (Oct physical planting)
- **Next physical action:** Order beds from byJEMA, build beds, plant W16 (mid-April)

### The Child
- Turning 7 (2026), ADHD and Autism
- Needs quick wins (5-10 min attention bursts), drawn to creatures/nature/counting/colors
- Engagement through task variety (dig, then water, then pick)
- His own beds, his own daily routine, increasing independence

### Family
- Vejle, Denmark. Some gardening basics.
- Daily time varies (5 min some days, hour+ weekends)
- 2-3 weeks mid-summer vacation (reservoirs + neighbor guide solve this)
- Budget: ~8,500-10,500 DKK total

### Technical
- Home Assistant running, Zigbee network established
- Sensor deployment planned for v2 (data schemas ready now)

## Constraints

- Danish zone 7b — growing season ~April-October
- Significant tree cover on east side limits full-sun in parts of backyard
- 2-3 week mid-summer vacation gaps — designed for with reservoirs + neighbor guide
- Child's 5-10 minute attention windows — all activities designed for this
- Budget: ~8,500-10,500 DKK total

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Raised beds over in-ground | Defined ownership ("his bed"), better soil control, accessible height | ✓ Good |
| Buy pre-made corten steel beds | Time efficiency, consistent quality, aesthetic preference | ✓ Good |
| Staggered planting for continuous harvest | Quick wins -- always something ready to pick | ✓ Good |
| Manual watering over irrigation | Watering IS the routine that builds agency | ✓ Good |
| Structured JSON data from day one | Enables HA integration, future visualizations, alerts | ✓ Good |
| Include crops he doesn't eat | Family beds round out the garden; his beds focus on his favorites | ✓ Good |
| Bed remapping (1-5 → A-E) | Phase 2 reshuffled bed assignments for better companion planting | ✓ Resolved in Phase 7 |
| Zinkbakken terrace beds | 80x40x40cm galvanized with capillary insert for deck protection | ✓ Good |
| Dual naming in Phase 1 docs | Bed N (Bed X) preserves build sequence while adding canonical identity | ✓ Good (Phase 7) |
| Tumbling Tom kept as backup | beds=[] with pot-only backup rather than deleting crop file | ✓ Good (Phase 7) |
| Danish cues as father-spoken prompts | Not child-readable text -- father reads aloud | ✓ Good (Phase 8) |
| Pick-2-of-4 weekly walk model | Child chooses activities for agency | ✓ Good (Phase 8) |
| Budget range ~8,500-10,500 DKK | Based on actual 2-bed shopping list totals | ✓ Good (Phase 9) |
| HA automations always-on year-round | Warm-season rules harmless when conditions unmet | ✓ Good (Phase 10) |
| Perennial care as standalone doc | Reusable from multiple contexts (end-of-season, troubleshooting) | ✓ Good (Phase 11) |
| vacation_note as optional schema field | Backward compatible with existing schedule files | ✓ Good (Phase 12) |

---
*Last updated: 2026-03-30 after v1.1 milestone*
