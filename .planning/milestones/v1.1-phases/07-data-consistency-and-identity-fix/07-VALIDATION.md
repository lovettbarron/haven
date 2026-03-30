---
phase: 7
slug: data-consistency-and-identity-fix
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-28
---

# Phase 7 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | Manual audit (no automated test framework for markdown/JSON consistency) |
| **Config file** | none |
| **Quick run command** | `python3 -m json.tool data/crops/dill.json > /dev/null && echo "valid JSON"` |
| **Full suite command** | `for f in data/crops/*.json data/beds/*.json data/ha/*.json; do python3 -m json.tool "$f" > /dev/null || echo "INVALID: $f"; done` |
| **Estimated runtime** | ~2 seconds |

---

## Sampling Rate

- **After every task commit:** JSON validation command on changed files
- **After every plan wave:** Full JSON validation + grep checks for stale references
- **Before `/gsd:verify-work`:** Full suite must be green
- **Max feedback latency:** 2 seconds

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 7-01-01 | 01 | 1 | DFIX-01 | manual | `grep -c "Bed [1-5]" docs/bed-layout.md docs/setup-guide.md docs/reservoir-build.md` (should be 0 standalone refs) | N/A | ⬜ pending |
| 7-01-02 | 01 | 1 | DFIX-02 | manual | `grep -A5 "Raised Beds" CLAUDE.md` visual check | N/A | ⬜ pending |
| 7-01-03 | 01 | 1 | DFIX-05 | manual | `grep -n "reservoir\|Beds A and B" docs/vacation-countdown-script.md` | N/A | ⬜ pending |
| 7-02-01 | 02 | 1 | DFIX-03 | manual | `python3 -c "import json; [print(f['id'], f['physical']['features']) for f in [json.load(open(f'data/beds/bed-{x}.json')) for x in 'abcde']]"` | N/A | ⬜ pending |
| 7-02-02 | 02 | 1 | DFIX-04 | manual | `grep -i "tomato\|tomat" data/ha/alert-rules.json` (should only appear in bed-c rules) | N/A | ⬜ pending |
| 7-02-03 | 02 | 1 | DFIX-06 | unit | `python3 -m json.tool data/crops/dill.json > /dev/null` | ❌ W0 | ⬜ pending |
| 7-02-04 | 02 | 1 | DFIX-07 | manual | `python3 -c "import json; print(json.load(open('data/crops/radish.json'))['beds'])"` | N/A | ⬜ pending |
| 7-03-01 | 03 | 1 | DFIX-08 | manual | `grep -n "lettuce.*Bed E" data/schedules/w2[5-9].json data/schedules/w3*.json` (should be 0) | N/A | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

- [ ] `data/crops/dill.json` — covers DFIX-06 (must be created as part of implementation)
- No test framework needed — this is an editorial/data correction phase

*Existing infrastructure covers all other phase requirements.*

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Phase 1 docs use Bed A-E naming | DFIX-01 | Semantic text edits in markdown | Grep for standalone "Bed [1-5]" references; verify mapping table exists |
| CLAUDE.md table matches grids | DFIX-02 | Cross-document consistency | Compare CLAUDE.md bed table against planting grid headers |
| HA alerts reference correct crops | DFIX-04 | JSON content semantics | Grep for tomato references outside bed-c rules |
| Vacation script correct reservoirs | DFIX-05 | Markdown content check | Verify reservoir bed references match actual reservoir beds |
| Radish beds documented | DFIX-07 | JSON content semantics | Verify beds array or exclusion note |
| No stale succession tasks | DFIX-08 | Schedule JSON content audit | Grep for stopped succession slots in future weeks |

---

## Validation Sign-Off

- [ ] All tasks have `<automated>` verify or Wave 0 dependencies
- [ ] Sampling continuity: no 3 consecutive tasks without automated verify
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency < 2s
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
