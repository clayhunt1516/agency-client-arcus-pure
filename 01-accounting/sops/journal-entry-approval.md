# Journal Entry Approval

> **Purpose:** Establish the approval workflow and audit trail for journal entries, ensuring entries are authorized at the appropriate level and supportable in audit.

## When to use this SOP

- **Triggered:** Any time a journal entry is drafted that requires approval before posting.
- **Excluded:** System-generated entries (recurring entries, AP/AR subledger postings, payroll postings) that follow pre-approved templates and don't require per-instance approval.

## Owner

- **Responsible:** Entry preparer (varies by entry type).
- **Accountable:** Controller (owns the approval matrix and audit trail).
- **Approver:** Per the matrix below.

## Inputs

- Drafted journal entry (in QuickBooks Online or workpaper).
- Supporting documentation (invoice, calculation, memo, etc.).
- Approval matrix (below).

## Approval matrix

| Entry type | Amount | Approver |
|---|---|---|
| Standard recurring (depreciation, prepaid amortization, scheduled accruals) | Any | Pre-approved via the recurring schedule; no per-instance approval needed |
| Routine adjustment (reclasses, corrections under threshold) | Under [threshold-low] | AP/AR specialist may post; reviewed retrospectively in trial balance review |
| Routine adjustment | [threshold-low] – [threshold-high] | Controller |
| Material adjustment (estimates, accrual changes, prior-period corrections) | Over [threshold-high] | Controller proposes; CFO approves |
| Closing entries (period-end accruals, deferrals, reserves) | Any | Controller |
| Restatements or out-of-period entries | Any | CFO; external auditor consulted if material |

Thresholds marked [threshold-low] and [threshold-high] are starting points — adjust to Arcus Pure's materiality threshold and segregation requirements once those are established [discovery].

## Steps

1. **Draft the entry.** Include: account numbers, debit/credit amounts, period, descriptive memo. The memo states the *reason* for the entry (the business rationale), not just what it does mechanically.
2. **Attach support.** Source documentation, calculations, or a memo explaining judgment if applicable. Insufficient support is grounds for the approver to return the entry.
3. **Determine approval level.** Match the entry to the matrix above based on type and amount.
4. **Submit for approval.** Through the ERP workflow or QuickBooks Online workflow. Include a link or reference to supporting documentation.
5. **Approver reviews.** Approver checks: account coding, period, amount, support adequacy, business reason. Approves or returns with comments.
6. **Post (if approved) or revise (if returned).** Posting locks the entry in the audit trail. Returns require revision and re-submission — never override a return without escalation.
7. **File documentation.** Supporting documentation goes to `/01-accounting/data/close-[YYYY-MM]/je-support/` (for closing entries) or to the relevant data subfolder (for in-period entries).

## Outputs

- Posted journal entry with approver name, date, and supporting documentation referenced.
- Audit trail in QuickBooks Online showing preparer, approver, timestamps.
- Supporting documentation filed in the appropriate `/data/` location.

## Quality check

- Every posted JE has a preparer, an approver (different person), and supporting documentation.
- No JE is posted by the same person who approved it (segregation of duties — non-negotiable).
- Memo describes the business reason, not just the mechanical effect.
- Material adjustments have a written justification beyond the memo, suitable for audit support.

## Common issues

- **Same person prepares and approves.** Hard stop. Find an alternative approver or escalate to Controller / CFO. Segregation of duties is non-negotiable.
- **Insufficient memo.** Approver returns with a request for clarification. Don't approve a vague entry — once posted, the audit trail is set.
- **Out-of-period entry needed.** Requires CFO approval and an explicit reason. May need disclosure if material. Default is to push the entry to the current open period if at all defensible.
- **System-generated entry posts incorrectly.** Investigate the recurring schedule or upstream subledger. Don't manually patch — fix the source so the issue doesn't recur.
- **Approver delays during close.** If an approval is blocking close, escalate to backup approver per the matrix. Do not extend the close window without Controller approval.
- **Discovery of a posting error after the period is locked.** Don't reopen unilaterally. Document the error, propose the correcting entry, route per the "Restatements or out-of-period entries" row.

## Related

- `/01-accounting/sops/ap-processing.md` — references this SOP for invoice approvals.
- `/01-accounting/sops/bank-reconciliation.md` — references this SOP for bank-driven JEs.
- `/01-accounting/sops/month-end-close.md` — references this SOP for Phase 3 adjustments.

---
- **Owner of this document:** Controller
- **Last reviewed:** 2026-05-25
- **Frequency:** Event-driven
