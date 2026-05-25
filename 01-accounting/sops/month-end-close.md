# Month-End Close

> **Purpose:** Close Arcus Pure's books for a fiscal period (typically a month) cleanly and on schedule, producing accurate financial statements and a complete close package.

## When to use this SOP

- **Scheduled:** Monthly, beginning the last business day of the period (Day 0).
- **Target:** Complete and distribute the monthly financial summary by Day [N] of the following month.

## Owner

- **Responsible:** Controller (orchestrator); subledger owners execute their phase.
- **Accountable:** CFO.
- **Approver:** CFO signs off on the closed period before lock.

## Inputs

- All operational subledger systems available and current (QuickBooks Online, [discovery], AP, AR).
- Prior month's close package (for comparison): `/01-accounting/data/close-[prior-YYYY-MM]/`.
- Budget for the period: `/06-executive/data/budget-[YYYY].csv`.
- Department-level commentary from in-scope department leads (collected in Phase 5).
- Materiality threshold per department CLAUDE.md.

## Steps

### Phase 1 — Pre-close cutoffs (Day 0, last business day of period)

1. **Send cutoff communications.** Email all departments by EOD Day 0. AP cutoff for vendor invoices: [discovery] on Day 1. AR billing cutoff: EOD Day 0. Expense reports: [discovery] on Day 1.
2. **Verify expected period-end transactions.** Pull the recurring-entries list (rent, subscriptions, depreciation calendar, scheduled accruals) and confirm each is posted or scheduled.
3. **Submit final manual entries.** Anything that needs to land in the closing period and isn't on the recurring schedule must be entered by EOD Day 0.

### Phase 2 — Subledger close (Day 1)

4. **AP close.** Per `/01-accounting/sops/ap-processing.md`: confirm all received-but-unpaid invoices for the period are entered. Book accruals for goods/services received but not yet invoiced.
5. **AR close.** Per `/01-accounting/sops/ar-aging-review.md`: confirm all customer invoices for the period are issued. Update deferred revenue.
6. **Bank reconciliation.** Per `/01-accounting/sops/bank-reconciliation.md`: reconcile each material bank account through the last business day of the period. Document outstanding items.
7. **Payroll accrual.** Book accrual for hours worked but not yet paid (typically the days between the last pay period end and period end).
8. **Inventory adjustment.** [discovery — confirm whether Arcus Pure carries inventory] If applicable: book cost-of-sales adjustments, count variances, and any obsolescence reserves. If not applicable, mark `N/A` in the close package.

### Phase 3 — GL adjustments (Day 2)

9. **Recurring entries posted.** Verify all recurring journal entries (depreciation, prepaid amortization, scheduled accruals) have posted. Reverse prior-period accruals where applicable.
10. **One-time adjustments.** Book any non-routine entries identified in Phase 2 or surfaced by management review. Each requires the approval workflow per `/01-accounting/sops/journal-entry-approval.md`.
11. **Intercompany.** Not applicable — Arcus Pure is single-entity. Mark `N/A` in close package.
12. **Tax provision.** [discovery — confirm whether Arcus Pure records a monthly tax provision] If yes: book based on YTD pre-tax income and effective rate. Otherwise mark `N/A` and defer to quarterly cadence.

### Phase 4 — Reconciliations and review (Day 3)

13. **Account reconciliations.** Reconcile each material balance sheet account against supporting documentation. At minimum: cash, AR, AP, accrued liabilities, payroll liabilities, prepaid expenses, fixed assets, debt. Save reconciliation files to `/01-accounting/data/close-[YYYY-MM]/`.
14. **Trial balance review.** Pull TB and confirm: assets = liabilities + equity, no abnormal balances (negative AR, positive AP), no entries posted to closed/restricted accounts.
15. **Variance analysis.** Compare current period to prior period and to budget. Investigate any variance over the materiality threshold; capture the explanation for the monthly summary.

### Phase 5 — Reporting and distribution (Day 4)

16. **Collect department commentary.** Email department leads requesting variance commentary for their areas. Deadline: EOD Day 4.
17. **Produce monthly financial summary.** Per the spec at `/01-accounting/reports/monthly-financial-summary.md`, produce the dated instance at `/01-accounting/reports/instances/monthly-financial-summary-[YYYY-MM].md`.
18. **Review with CFO.** CFO reviews and approves the summary before distribution. Address any flagged questions before sending.
19. **Distribute.** Follow the distribution rules in the report spec (email `leadership@`, post in [discovery]).

### Phase 6 — Close lock (Day [N])

20. **Lock the period in the ERP.** No further entries to the closed period without explicit Controller approval and a documented reason.
21. **Archive the close package.** Confirm `/01-accounting/data/close-[YYYY-MM]/` contains all reconciliations, supporting docs, and the final TB. Structure preserved.
22. **Brief retrospective.** Note any process issues or ambiguities encountered in `/01-accounting/data/close-[YYYY-MM]/notes.md`. If something should change in this SOP, propose the change at the next review cycle.

## Outputs

- `/01-accounting/data/close-[YYYY-MM]/` folder containing reconciliations, supporting documentation, final trial balance, and retrospective notes.
- `/01-accounting/reports/instances/monthly-financial-summary-[YYYY-MM].md` — produced and distributed.
- ERP period locked.
- Trial balance final and clean.

## Quality check

- Trial balance balances to zero.
- All material accounts (per the checklist in `/01-accounting/CLAUDE.md`) have reconciliation files in `/data/close-[YYYY-MM]/`.
- Monthly financial summary produced and distributed within the target close window.
- No unexplained variances over materiality threshold left open.
- Period is locked in the ERP.

## Common issues

- **AP invoices arrive after cutoff.** Decide whether to accrue (if material) or push to next period (if immaterial). Document the decision in close notes.
- **Bank rec doesn't tie.** Investigate before continuing — usually timing differences (deposits in transit, outstanding checks), but could be entry errors. Don't override.
- **Recurring entry didn't post.** Manually post and investigate the cause. If a system issue, escalate to whoever maintains the recurring entry schedule.
- **Department commentary delayed.** Controller produces the report with placeholders for the missing commentary and a clear flag (e.g., *"[Sales commentary pending — will follow]"*). Don't hold the close.
- **Material variance with no explanation available by Day 4.** Don't ship the summary without acknowledgment. Either delay distribution by 1 day with explicit notice, or ship with the variance flagged as *"investigation pending — target resolution [date]."*
- **Period needs to be reopened after lock.** Document the reason, the entry being added, and obtain CFO approval before reopening. Re-distribute an updated summary if the change is material.

## Related

- `/01-accounting/sops/ap-processing.md` — subledger close (upstream of step 4).
- `/01-accounting/sops/ar-aging-review.md` — subledger close (upstream of step 5).
- `/01-accounting/sops/bank-reconciliation.md` — subledger close (upstream of step 6).
- `/01-accounting/sops/journal-entry-approval.md` — governance for adjustments in Phase 3.
- `/01-accounting/reports/monthly-financial-summary.md` — primary output of this SOP.

---
- **Owner of this document:** Controller
- **Last reviewed:** 2026-05-25
- **Frequency:** Monthly
