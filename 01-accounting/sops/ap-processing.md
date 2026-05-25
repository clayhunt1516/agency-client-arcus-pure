# AP Processing

> **Purpose:** Move vendor invoices from receipt to payment cleanly and on terms, while ensuring proper approval, accurate GL coding, and a complete audit trail.

## When to use this SOP

- **Continuous (Phases 1–2):** Whenever an invoice arrives.
- **Scheduled (Phase 3):** Payment run on [discovery — day/schedule].
- **Period-end (Phase 4):** Last business day of the period and Day 1 after — feeds month-end close.

## Owner

- **Responsible:** AP specialist / [discovery].
- **Accountable:** Controller / [discovery].
- **Approver:** Per the approval matrix in `/01-accounting/sops/journal-entry-approval.md` for invoices over thresholds; department leads for departmental expenses.

## Inputs

- Vendor invoices received via [discovery — intake channels].
- Vendor master in QuickBooks Online (W-9, payment details, terms).
- Open POs in QuickBooks Online for matched invoices.
- Approval matrix per `/01-accounting/sops/journal-entry-approval.md`.

## Steps

### Phase 1 — Invoice intake & coding (continuous)

1. **Receive and triage.** Pull invoices from [discovery]. Confirm each is a real invoice (not a statement, reminder, or duplicate).
2. **Verify vendor.** Confirm the vendor is on file with current W-9 and payment details. If not, route to vendor onboarding before proceeding.
3. **Check for duplicates.** Search the ERP by invoice number and amount. If duplicate, return to vendor with a note; do not enter.
4. **Match to PO (if applicable).** For vendors on PO terms, three-way match: invoice ↔ PO ↔ receiving record. Discrepancies route to [discovery] for resolution before entry.
5. **Enter into AP module.** Code to GL account and cost center per the chart of accounts. Attach the invoice file.
6. **Set due date.** Per vendor terms (Net 30, Net 15, etc.). Note any early-pay discounts.

### Phase 2 — Approval (continuous)

7. **Determine approval level.** Per the matrix in `/01-accounting/sops/journal-entry-approval.md`, route based on amount, account, and vendor.
8. **Submit for approval.** Through the ERP workflow or QuickBooks Online workflow.
9. **Resolve issues.** If rejected: address feedback (reclassify, request additional documentation, return to vendor). If approved: invoice is now payable.

### Phase 3 — Payment runs (scheduled)

10. **Pull payment list.** On [discovery], pull all approved invoices with due dates within the payment window ([discovery]).
11. **Confirm cash availability.** Compare payment list total to current cash balance. If insufficient, escalate to Controller for prioritization.
12. **Process payments.** Issue payments per vendor preference (ACH, check, wire). Save remittance details.
13. **Send remittance advice.** Email or upload remittance to vendor portals where required.
14. **Update ERP.** Confirm each payment is marked Paid with the correct payment date and reference.

### Phase 4 — Period-end review (last day of period + Day 1)

15. **Confirm all period invoices entered.** Pull list of received-but-unentered invoices. Enter anything dated in the closing period.
16. **Book accruals.** For goods or services received but not yet invoiced, book accrual entries per the standard accrual list. Reverse next period.
17. **Reconcile AP subledger to GL.** AP control account should equal AP subledger total. Investigate any variance before close handoff.
18. **Hand off to month-end close.** Per `/01-accounting/sops/month-end-close.md` Phase 2 step 4.

## Outputs

- Each invoice entered, coded, approved, and paid (or accrued) in the ERP with full audit trail.
- Remittance advices sent to vendors per their preferences.
- AP subledger reconciled to GL at period end.
- Accrual entries posted (and reversed in the following period).

## Quality check

- No duplicate payments (verify via the ERP's duplicate-check report).
- AP aging shows nothing past due that wasn't deliberately deferred (with documented reason).
- AP subledger ties to GL at period end (within $1).
- Every approved invoice has a documented approver in the audit trail.
- Vendor master changes (new vendors, banking detail updates) follow segregation of duties: requested by AP, approved by Controller.

## Common issues

- **Invoice without PO for a vendor on PO terms.** Hold and route to purchasing for retroactive PO or written explanation. Don't pay until resolved.
- **Vendor sends statement, not invoice.** Don't enter — request the actual invoice. Statements are summaries, not payable documents.
- **Approver out of office.** Per approval matrix, escalate to backup approver. Don't bypass.
- **Vendor banking details change request.** Treat as fraud risk. Verify by phone with a known contact, not the email requesting the change. Document the verification before updating.
- **Cash insufficient on payment day.** Controller prioritizes. General order: payroll-related first, critical operating vendors second, others deferred with vendor communication.
- **Duplicate payment caught after issuance.** Contact vendor immediately, request return, document the incident and root cause, update controls if recurring.

## Related

- `/01-accounting/sops/journal-entry-approval.md` — approval matrix and routing.
- `/01-accounting/sops/month-end-close.md` — Phase 2 step 4 references this SOP.
- `/01-accounting/sops/vendor-onboarding.md` — required before paying a new vendor (when this SOP exists).
- `/01-accounting/reports/ap-aging-summary.md` — periodic AP health report (when this report exists).

---
- **Owner of this document:** Controller
- **Last reviewed:** 2026-05-25
- **Frequency:** Continuous (Phases 1–2), scheduled (Phase 3), monthly (Phase 4)
