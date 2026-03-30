---
phase: 11
slug: season-2-preparation
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-28
---

# Phase 11 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | Manual review (documentation project, no executable code) |
| **Config file** | none |
| **Quick run command** | `ls docs/end-of-season-guide.md docs/perennial-care.md docs/soil-refresh-guide.md docs/season-review-template.md data/schemas/season-review.schema.json` |
| **Full suite command** | Manual review: verify all 5 deliverables exist and cross-references resolve |
| **Estimated runtime** | ~2 seconds (file existence checks) |

---

## Sampling Rate

- **After every task commit:** `ls -la` on expected output files
- **After every plan wave:** Manual review of all deliverables + cross-reference check
- **Before `/gsd:verify-work`:** All 5 deliverables exist, troubleshooting guide extended, JSON schema valid
- **Max feedback latency:** 2 seconds

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 11-01-01 | 01 | 1 | SSN2-01 | smoke | `test -f docs/end-of-season-guide.md && grep -q "reservoir" docs/end-of-season-guide.md` | ❌ W0 | ⬜ pending |
| 11-01-02 | 01 | 1 | SSN2-02 | smoke | `test -f docs/perennial-care.md && grep -q "strawberry" docs/perennial-care.md` | ❌ W0 | ⬜ pending |
| 11-01-03 | 01 | 1 | SSN2-03 | smoke | `test -f docs/soil-refresh-guide.md && grep -q "hojbedsmuld" docs/soil-refresh-guide.md` | ❌ W0 | ⬜ pending |
| 11-02-01 | 02 | 1 | SSN2-04 | smoke | `test -f docs/season-review-template.md && test -f data/schemas/season-review.schema.json` | ❌ W0 | ⬜ pending |
| 11-02-02 | 02 | 1 | SSN2-05 | smoke | `grep -q "Crop Failure" docs/troubleshooting-guide.md` | ❌ W0 | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

*Existing infrastructure covers all phase requirements. No test framework needed — documentation-only phase uses file existence smoke checks.*

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Cleanup guide covers W44-W46 tasks comprehensively | SSN2-01 | Content quality cannot be automated | Review guide has sections for plant removal, composting, reservoir draining, tool storage |
| Perennial notes are accurate for specific varieties | SSN2-02 | Horticultural accuracy check | Verify Autumn Bliss raspberry notes say February pruning, strawberry notes specify mulching after hard frosts |
| Soil refresh amounts are correct for bed dimensions | SSN2-03 | Calculation accuracy | Verify compost amounts match 230×120 and 150×60 bed dimensions |
| Season review template is ADHD-friendly | SSN2-04 | Usability for neurodivergent child | Check template has clear structure, visual ratings, minimal open-ended writing |
| Crop failure recovery windows are regionally accurate | SSN2-05 | Zone 7b maritime timing | Verify replanting windows align with Danish growing season (W16-W44) |

---

## Validation Sign-Off

- [ ] All tasks have `<automated>` verify or Wave 0 dependencies
- [ ] Sampling continuity: no 3 consecutive tasks without automated verify
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency < 2s
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
