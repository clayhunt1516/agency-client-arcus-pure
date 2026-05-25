# AP Aging Summary

> **Purpose:** Track payables health weekly so payment timing is intentional, vendor relationships are maintained, and cash is deployed against obligations on terms.

## Spec

- **Audience:** Controller, AP specialist. CFO/owner included on payment prioritization decisions when cash is constrained.
- **Cadence:** Weekly, aligned with payment-run prep ([discovery]).
- **Owner:** AP specialist (production).
- **Reviewer / approver:** Controller (review before payment run).
- **Source data:**
  - Current AP aging snapshot: `/01-accounting/data/ap-aging-2026-05-25.csv`
  - Prior week's snapshot: `/01-accounting/data/ap-aging-[prior-YYYY-MM-DD].csv`
  - Vendor master (terms, early-pay discounts).
  - Cash position from `/01-accounting/reports/instances/cash-flow-2026-05-25.md`.
- **Produced by SOP:** `/01-accounting/sops/ap-processing.md` Phase 3 step 10.
- **Output location:** `/01-accounting/reports/instances/ap-aging-summary-2026-05-25.md`
- **Distribution:** Email to Controller. Post in [discovery].

## Structure

### Headline

One paragraph: total AP balance, week-over-week direction, past-due status, recommended payment list for this week's run.

### Key figures

| Metric | This week | Prior week | Change |
|---|---|---|---|
| Total AP | | | |
| AP current (not yet due) | | | |
| AP 1–30 days past due | | | |
| AP 31–60 days past due | | | |
| AP 60+ days past due | | | |

### Recommended payment list

Approved invoices due within [discovery — payment window]. For each:

- **[Vendor]** — [$ amount], due [date].
  - Terms: [Net X].
  - Early-pay discount available: [yes — terms / no].
  - Payment method: [ACH / check / wire].
  - Notes: [any special handling].

Total recommended for this run: [$ total].

### Past-due items

Any invoice past its due date. For each:

- **[Vendor]** — [$ amount], [N] days past due.
  - Reason: [cash deferral / dispute / awaiting approval / other].
  - Action: [pay this run / continue deferral / resolve dispute].
  - Owner: [discovery].

If none, state explicitly: *"No invoices past due this week."*

### Discounts available

Invoices with early-pay discounts available in the next 14 days. Quantify discount value (in dollars, not just terms).

### Concerns

Vendor relationship issues, escalations, or anything Controller should know before signing the payment run.

### Methodology / sources

- Snapshot date: 2026-05-25.
- Source files: listed in spec above.
- Reconciliation note: confirm AP snapshot total ties to GL AP control account (within $1).

---
- **Maintainer of this spec:** Controller
- **Last reviewed:** 2026-05-25
- **Cadence:** Weekly
