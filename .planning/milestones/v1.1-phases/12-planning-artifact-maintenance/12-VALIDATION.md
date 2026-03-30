---
phase: 12
slug: planning-artifact-maintenance
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-28
---

# Phase 12 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | grep + JSON schema validation (node) |
| **Config file** | data/schemas/week.schema.json |
| **Quick run command** | `grep -c '\[ \]' .planning/ROADMAP.md` |
| **Full suite command** | `node -e "const fs=require('fs');const s=JSON.parse(fs.readFileSync('data/schemas/week.schema.json'));console.log('schema OK')" && grep -c 'Pending' .planning/REQUIREMENTS.md` |
| **Estimated runtime** | ~2 seconds |

---

## Sampling Rate

- **After every task commit:** Run `grep -c '\[ \]' .planning/ROADMAP.md` + check target file
- **After every plan wave:** Full audit of all 5 target files
- **Before `/gsd:verify-work`:** Full suite must be green
- **Max feedback latency:** 2 seconds

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 12-01-01 | 01 | 1 | PMNT-01 | manual | `grep -c '\[ \]' .planning/ROADMAP.md` | N/A | ⬜ pending |
| 12-01-02 | 01 | 1 | PMNT-02 | manual | `grep 'Revisit' .planning/PROJECT.md` | N/A | ⬜ pending |
| 12-01-03 | 01 | 1 | PMNT-03 | manual | `grep 'Pending' .planning/REQUIREMENTS.md` | N/A | ⬜ pending |
| 12-02-01 | 02 | 1 | PMNT-04 | manual | Check w30-w33 for vacation_note field | N/A | ⬜ pending |
| 12-02-02 | 02 | 1 | PMNT-05 | manual | Check w40.json hero_task alignment | N/A | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

Existing infrastructure covers all phase requirements. No test framework install needed — all validation is grep-based or manual JSON inspection.

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| ROADMAP checkboxes match completion | PMNT-01 | Checkbox semantics require human judgment | Grep for `[ ]`, verify only Phase 12 items remain unchecked |
| PROJECT.md decisions updated | PMNT-02 | Decision outcome text is free-form | Grep for `Revisit` or `Pending`, verify 0 stale entries |
| REQUIREMENTS.md traceability | PMNT-03 | Status text is contextual | Check DOCS-04 and COOK-02 rows specifically |
| Vacation week neighbor flag | PMNT-04 | Schema + data change validation | Validate w30-w33 JSONs have vacation_note field |
| W40 garlic alignment | PMNT-05 | Content alignment with garlic plan | Compare w40.json with garlic-autumn-plan.md |

---

## Validation Sign-Off

- [ ] All tasks have `<automated>` verify or Wave 0 dependencies
- [ ] Sampling continuity: no 3 consecutive tasks without automated verify
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency < 2s
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
