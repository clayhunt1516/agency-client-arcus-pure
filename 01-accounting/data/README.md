# `/01-accounting/data/` — Reference Data

This folder holds reference data, exports, and snapshots from Arcus Pure's financial systems. These files are **inputs** to SOPs and reports — they are NOT the system of record.

## What goes here

- **ERP exports.** Periodic exports from QuickBooks Online (GL exports, AR/AP aging, trial balances). One file per export, dated.
- **Bank statements.** Monthly bank statements and supporting reconciliation files.
- **Reference tables.** Chart of accounts, cost center map, vendor master snapshot, customer master snapshot.
- **Supporting documentation.** Source documents that back specific journal entries (invoices, expense reports, contracts) — typically organized in dated subfolders.
- **Anything else needed to support an SOP or to audit a number in a report.**

## What does NOT go here

- **Live system data.** The ERP, bank, payroll, etc. are the systems of record. Don't try to mirror them — pull when needed.
- **Generated reports.** Those go in `/01-accounting/reports/`.
- **SOPs or other documentation.** Those go in `/01-accounting/sops/`.
- **Personal or sensitive files.** No PII (SSNs, full bank account numbers), credentials, or anything that shouldn't exist in a Git-tracked structure. Even though the contents of this folder are gitignored (see below), assume any file might leak and act accordingly.

## Naming convention

`[descriptor]-[YYYY-MM-DD or YYYY-MM].[ext]`

Examples:
- `ar-aging-2025-11-04.csv`
- `gl-export-2025-10.csv`
- `bank-statement-mainacct-2025-10.pdf`
- `chart-of-accounts-2025-11.csv`

Always include a date in the filename. The export date is part of the file's identity — without it, the file is meaningless six weeks from now.

For supporting documentation tied to a specific period, use a dated subfolder:

```
close-2025-10/
├── bank-rec-mainacct.xlsx
├── payroll-accrual-support.pdf
└── inventory-count-adjustments.csv
```

## Operating rules

1. **Read-only.** Files in this folder are written by export or import processes; they are not edited by hand. If a file needs correction, fix the source system and re-export — don't fix the file in place.
2. **Don't trust the snapshot for current state.** A file dated `2025-11-04` reflects state as of that date. For "what is true right now," go to the live system.
3. **Cite the file when using its data.** When a calculation or report cites a number from this folder, cite the file path and date (e.g., *"AR balance is $X as of 2025-11-04 per `/01-accounting/data/ar-aging-2025-11-04.csv`."*).

## Git behavior

The contents of this folder are excluded from Git via `.gitignore` (`**/data/*` with `!**/data/.gitkeep` and `!**/data/README.md` exceptions). The folder structure is preserved; the data itself is not tracked. This is intentional:

- Data files can contain sensitive information.
- Data files change frequently and would bloat Git history.
- Data files are reproducible from source systems — Git is the wrong place to back them up.

If a specific data file needs to be shared across team members or AI sessions, use a separate sync mechanism (cloud storage, shared drive) — not Git.
