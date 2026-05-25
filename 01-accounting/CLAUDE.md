# Accounting — Department Knowledge

> **For Claude:** This file is the entry point for Arcus Pure's accounting department. Read it before working in any subfolder of `/01-accounting/`. Root-level operating principles still apply; this file adds department-specific context.

---

## What this department does

The accounting department is responsible for Arcus Pure's financial operations: recording transactions, managing receivables and payables, closing the books, producing financial reports, ensuring controls and compliance, and supporting tax and audit functions.

This is a back-office function with strict accuracy requirements. Errors cascade — a misposted journal entry distorts financial statements, which distorts tax filings, which distorts trust with stakeholders. Default to slow-and-correct over fast-and-uncertain.

## Who owns what

| Role | Owner | Scope |
|---|---|---|
| Department lead | [discovery] | Overall responsibility, sign-off authority |
| AP | [discovery] | Vendor invoices, payments, expense reimbursements |
| AR | [discovery] | Customer invoices, collections, aging |
| GL / month-end | [discovery] | Journal entries, reconciliations, close |
| Reporting | [discovery] | Monthly financials, KPI reports, board materials |
| Tax / compliance | [discovery] | Filings, audit support, regulatory work |

For full org context and decision rights, see Notion → Company Overview.

## Department-specific terminology

- **Close** — finalizing the books for a period (typically a month). "Soft close" is preliminary; "hard close" is final and locked.
- **AR aging** — receivables grouped by how long they've been outstanding (current, 30, 60, 90+ days).
- **AP aging** — payables grouped the same way.
- **GL** — general ledger; the master record of all journal entries.
- **Reconciliation** — matching internal records to an external source (typically a bank statement).
- **Materiality threshold** — the dollar amount or percentage above which a variance, error, or transaction warrants explanation. Arcus Pure's threshold: [discovery]

For company-wide glossary, see Notion → Company Overview → Glossary.

## Authoritative systems and data freshness

- **System of record:** QuickBooks Online.
- **Bank data:** [discovery]
- **Payroll:** [discovery]
- **Expense management:** [discovery]
- **Files in `/01-accounting/data/`:** exports and snapshots from the systems above. They are NOT the system of record. Each file's export date is in its filename (`ar-aging-2025-11-04.csv`) or header. For real-time numbers, point to the live system.

## What "good" looks like

- **Month-end close** completes within [discovery] business days of period end.
- **AR aging** is reviewed weekly; nothing 90+ days goes unaddressed.
- **AP** is paid on standard terms ([discovery] days) unless there is a documented reason to delay.
- **Reconciliations** for material accounts (cash, AR, AP, payroll liabilities, intercompany) are signed off before the close is called done.
- **Variance analysis** in the monthly report explains anything moving more than [discovery] versus prior period or budget.
- **Audit trail:** every journal entry has a clear description of the reason, supporting documentation in `/data/`, and a documented approver.

## Folder structure

| Path | Purpose |
|---|---|
| `/01-accounting/sops/` | Standard operating procedures. One file per process. |
| `/01-accounting/reports/` | Report templates and recurring report specifications. |
| `/01-accounting/data/` | Read-only exports and reference data from the ERP and other systems. |

## Key SOPs

- `/01-accounting/sops/month-end-close.md` — close calendar and step-by-step procedure.
- `/01-accounting/sops/ar-aging-review.md` — weekly receivables review.
- `/01-accounting/sops/ap-processing.md` — vendor invoice handling.
- `/01-accounting/sops/bank-reconciliation.md` — bank rec procedure.
- `/01-accounting/sops/journal-entry-approval.md` — JE submission and approval flow.

## Department-specific operating rules

These extend (do not replace) the root-level operating principles.

1. **Never modify accounting data files.** Even more strictly than the universal rule: anything in `/01-accounting/data/` is sacred. If a calculation needs source data, read it; never edit it.
2. **Cite figures with their source and date.** When stating a financial number, include the source file and the date of the export. Example: *"AR balance is $X as of 2026-05-25 per `/01-accounting/data/ar-aging-2026-05-25.csv`."*
3. **Flag period-end ambiguity.** If a question spans a period boundary (mid-close, fiscal year-end, etc.), explicitly note which period the answer applies to.
4. **Don't infer materiality.** If asked "is this a big number," don't guess — point to the materiality threshold and let the user decide.
5. **Round consistently.** Default to thousands ($K) for financial summaries unless precision is requested. Always show the unit (`$1,250K` not `$1,250`).
6. **Distinguish accrual from cash.** When discussing financial figures, be explicit about whether they're accrual-basis or cash-basis. Don't blend.

---
- **Maintainer of this file:** [discovery]
- **Last reviewed:** 2026-05-25
