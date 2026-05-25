# Bank Reconciliation

> **Purpose:** Reconcile each material bank account's statement balance to the GL cash balance, surfacing timing differences and catching errors before they propagate to financial statements.

## When to use this SOP

- **Scheduled:** Monthly, as soon as the bank statement is available for the closed period (typically Day 1–2 of the following period).
- **Triggered:** Whenever a material discrepancy is suspected — unexpected bank balance, missing transactions, returned items.

## Owner

- **Responsible:** AP specialist or designated cash specialist / [discovery].
- **Accountable:** Controller / [discovery].
- **Approver:** Controller signs off on each completed reconciliation before the close is called done.

## Inputs

- Bank statement for the period (PDF or feed) saved to `/01-accounting/data/bank-statement-[account-name]-[YYYY-MM].pdf`.
- GL cash account activity for the same period (export from QuickBooks Online).
- Prior period's reconciliation, for outstanding items rolling forward: `/01-accounting/data/close-[prior-YYYY-MM]/bank-rec-[account].xlsx`.
- List of material bank accounts per `/01-accounting/CLAUDE.md`.

## Steps

1. **Pull bank statement and GL activity.** Save the statement to the data folder per the naming convention. Export GL activity for the cash account through period end.
2. **Confirm beginning balance ties.** Bank statement opening balance should match prior period's reconciled bank balance. If not, investigate the prior reconciliation before continuing — do not proceed.
3. **Match transactions.** For each cleared transaction on the bank statement, find the corresponding GL entry. Mark both as reconciled.
4. **Identify outstanding items.** Items in the GL but not on the statement (deposits in transit, outstanding checks). List with date and amount.
5. **Identify bank-only items.** Items on the statement but not in the GL (bank fees, interest, automatic transfers, returned items). For each, determine whether it requires a GL entry.
6. **Book missing GL entries.** Per `/01-accounting/sops/journal-entry-approval.md`, post entries for bank-only items that should be in the GL. Re-export GL activity after posting.
7. **Calculate adjusted balances.** Reconciled bank balance = statement ending balance + deposits in transit − outstanding checks. Reconciled GL balance = GL ending balance with all required adjustments posted. The two should match exactly.
8. **Document the reconciliation.** Save the reconciliation worksheet to `/01-accounting/data/close-[YYYY-MM]/bank-rec-[account].xlsx` containing: statement balance, outstanding items list, GL adjustments posted, adjusted balance, sign-off line.
9. **Submit for Controller review.** Controller reviews the worksheet and signs off (date and name in the worksheet) before the rec is considered complete.

## Outputs

- Reconciliation worksheet at `/01-accounting/data/close-[YYYY-MM]/bank-rec-[account].xlsx`.
- Any required JEs posted via `/01-accounting/sops/journal-entry-approval.md`.
- Controller sign-off recorded in the worksheet.

## Quality check

- Reconciled bank balance equals adjusted GL balance, exact (no $0.01 variance acceptable for a final rec).
- All outstanding items have explanations and target clear-by dates.
- No outstanding check older than 6 months without a documented reason (escheatment risk).
- Controller sign-off present in the worksheet.

## Common issues

- **Beginning balance doesn't tie.** Prior reconciliation has an error or wasn't fully signed off. Don't continue — fix the prior period first.
- **Outstanding check from a prior period still outstanding.** Contact vendor to confirm receipt; if lost, void and reissue. Escheatment rules vary by state — escalate stale items to Controller.
- **Unidentifiable transaction on bank statement.** Pull bank documentation (memo, image of cleared check). If still unclear, contact the bank. Don't post a guess.
- **Bank statement total off from sum of transactions.** Bank error (rare) or reading error (more likely). Recheck. Contact bank if confirmed.
- **Returned items (NSF, ACH return).** Reverse the deposit, contact AR per `/01-accounting/sops/ar-aging-review.md`, charge back any associated fees.

## Related

- `/01-accounting/sops/journal-entry-approval.md` — required for any GL adjustments identified during reconciliation.
- `/01-accounting/sops/month-end-close.md` — Phase 2 step 6 requires this SOP complete.
- `/01-accounting/CLAUDE.md` — list of material accounts requiring reconciliation.

---
- **Owner of this document:** Controller
- **Last reviewed:** 2026-05-25
- **Frequency:** Monthly
