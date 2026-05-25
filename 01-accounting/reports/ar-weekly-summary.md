# AR Weekly Summary

> **Purpose:** Track receivables health weekly so collection issues are addressed before they become writeoffs, and so leadership has a current picture of cash inflow risk.

## Spec

- **Audience:** Controller, AR specialist; Sales lead is included on accounts where they own the customer relationship.
- **Cadence:** Weekly, every [discovery].
- **Owner:** AR specialist (production).
- **Reviewer / approver:** Controller (review before distribution).
- **Source data:**
  - Current AR aging snapshot: `/01-accounting/data/ar-aging-2026-05-25.csv`
  - Prior week's snapshot: `/01-accounting/data/ar-aging-[prior-YYYY-MM-DD].csv`
  - Customer master data: credit limits, payment terms (from QuickBooks Online)
  - Collection contact log (from [discovery])
- **Produced by SOP:** `/01-accounting/sops/ar-aging-review.md`
- **Output location:** `/01-accounting/reports/instances/ar-weekly-summary-2026-05-25.md`
- **Distribution:** Email to Controller; for accounts requiring sales involvement, also email the relevant Sales lead. Post in [discovery].

## Structure

### Headline

One paragraph: total AR position, week-over-week direction, any accounts that moved into a more-overdue bucket, anything urgent. If the week was uneventful, say so explicitly.

### Key figures

| Metric | This week | Prior week | Change |
|---|---|---|---|
| Total AR | | | |
| AR current | | | |
| AR 30–60 days | | | |
| AR 60–90 days | | | |
| AR 90+ days | | | |
| Number of accounts > 60 days | | | |

### Accounts requiring action

List of accounts 60+ days overdue. For each:

- **[Customer name]** — [$ balance], [N] days overdue.
  - Last contact: [date and outcome].
  - Action this week: [outreach / escalation / writeoff recommendation].
  - Owner: [discovery].

If no accounts meet this threshold, state explicitly: *"No accounts over 60 days outstanding this week."*

### Newly overdue this week

Accounts that crossed into a more-overdue bucket since last week (current → 30, 30 → 60, 60 → 90, 90+). For each, name the cause if known: timing issue, payment failure, dispute, customer financial distress, etc.

### Collected this week

Accounts that paid in full or moved to a less-overdue bucket. Highlight any collection that materially changes the AR position.

### Open items

Action items from this report. Each has an owner, a target date, and a one-line description.

### Methodology / sources

- Snapshot date: 2026-05-25.
- Prior snapshot date: 2026-05-25.
- Source files: listed in spec above.
- Reconciliation note: confirm snapshot total ties to GL AR control account within $1. Note any variance and resolution.

---
- **Maintainer of this spec:** Controller
- **Last reviewed:** 2026-05-25
- **Cadence:** Weekly
