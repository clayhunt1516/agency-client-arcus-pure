# AR Aging Review

> **Purpose:** Surface and address overdue receivables on a weekly cadence so Arcus Pure maintains healthy cash flow and addresses collection issues before they become writeoffs.

## When to use this SOP

Every [discovery — day of week] morning, before the AR team's weekly standup. Also as-needed when leadership requests a current AR snapshot (note: an ad-hoc snapshot does not replace the weekly review).

## Owner

- **Responsible:** AR specialist / [discovery]
- **Accountable:** Controller / [discovery]
- **Approver (for writeoff recommendations):** Controller

## Inputs

- Access to QuickBooks Online with the AR module enabled.
- Customer master data (current credit limits, payment terms).
- Prior week's AR aging snapshot for comparison, in `/01-accounting/data/`.
- Notes from any customer collection conversations in the last week (CRM or shared inbox).

## Steps

1. **Pull the current AR aging report.** In QuickBooks Online, run the standard AR aging report as of today. Export to CSV and save to `/01-accounting/data/ar-aging-2026-05-25.csv`.
2. **Compare to prior week's snapshot.** Note any accounts that moved into a more-overdue bucket (current → 30, 30 → 60, 60 → 90, 90+).
3. **Review accounts 60+ days overdue.** For each:
   - Pull the customer's payment history.
   - Confirm whether contact has been made in the last 14 days.
   - If no contact: schedule outreach this week.
   - If contact made but no resolution: escalate to Controller.
4. **Review accounts 90+ days overdue.** For each:
   - Check whether the receivable is disputed (look for support tickets, email threads, contract questions).
   - If undisputed and >90 days: prepare a writeoff recommendation for Controller approval at month-end.
5. **Summarize the week-over-week movement.** Write a 3–5 line summary to `/01-accounting/reports/ar-weekly-summary-2026-05-25.md` covering: total AR, change from prior week, accounts newly overdue, accounts collected.

## Outputs

- `/01-accounting/data/ar-aging-2026-05-25.csv` — current snapshot.
- `/01-accounting/reports/ar-weekly-summary-2026-05-25.md` — narrative summary.
- Outreach scheduled in [discovery] for flagged accounts.
- Writeoff recommendations queued for Controller review (if any).

## Quality check

- The snapshot CSV total matches the GL AR control account balance (within $1; small rounding is acceptable, large variance indicates a sub-ledger issue and should be escalated to GL/month-end owner before continuing).
- Every account 60+ days has a contact note dated within the last 14 days OR an action item created today.
- The weekly summary report exists, is dated correctly, and is readable as standalone narrative.

## Common issues

- **Customer disputes a charge mid-cycle.** Don't include in writeoff recommendations until the dispute is resolved or 60 days past the dispute being raised. Flag in the summary and link to the dispute thread.
- **Aging report doesn't match subledger.** Possible unposted entries. Hold off on the review until the close team reconciles, then redo.
- **Account marked "do not contact" by Sales.** Don't outreach. Escalate to Controller and Sales lead jointly to determine next step.

## Related

- `/01-accounting/sops/customer-credit-review.md` — for accounts showing repeated late-payment patterns.
- `/01-accounting/sops/writeoff-procedure.md` — for executing approved writeoffs.
- `/01-accounting/reports/ar-weekly-summary-2026-05-25.md` — output of this SOP, becomes input to month-end reporting.

---
- **Owner of this document:** Controller
- **Last reviewed:** 2026-05-25
- **Frequency:** Weekly
