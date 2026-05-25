# Budget vs Actual

> **Purpose:** Give department leads and finance leadership a complete line-by-line view of how the period's results compare to budget, supporting both performance management and financial control.

## Spec

- **Audience:** Department leads (their lines), Controller, CFO. Full report goes to leadership; departmental excerpts go to each department lead.
- **Cadence:** Monthly, distributed within [discovery] business days of month-end close (one day after the monthly financial summary so the executive narrative reaches leadership first).
- **Owner:** Controller (production), with input from FP&A and department leads on commentary.
- **Reviewer / approver:** CFO before distribution.
- **Source data:**
  - GL export for the closed period: `/01-accounting/data/gl-export-[YYYY-MM].csv`
  - Budget for the period: `/06-executive/data/budget-[YYYY].csv`
  - Prior year actuals (for YoY comparison): `/01-accounting/data/gl-export-[prior-YYYY-MM].csv`
  - Department lead commentary on variances.
- **Produced by SOP:** `/01-accounting/sops/month-end-close.md` (final reporting phase, after monthly financial summary).
- **Output location:** `/01-accounting/reports/instances/budget-vs-actual-[YYYY-MM].md`
- **Distribution:** Email full report to leadership; departmental excerpts to each department lead.

## Structure

### Headline

One paragraph: overall period vs budget — favorable, unfavorable, mixed? What's the dominant story? Anything trending unusually relative to YTD?

### Summary by department

| Department | Budget | Actual | $ variance | % variance | YTD variance |
|---|---|---|---|---|---|
| Service | | | | | |
| Sales | | | | | |
| Inventory / COGS | | | | | |
| Marketing | | | | | |
| G&A (incl. Accounting) | | | | | |
| **Total** | | | | | |

### Revenue detail

Line-by-line revenue breakdown. For each line: period actual, period budget, $ variance, % variance, prior-year same-period actual, YTD actual vs YTD budget.

### Operating expense detail

Line-by-line operating expense breakdown by department. Same columns as revenue detail.

### Variance commentary

Every line item with variance over [materiality threshold] gets an explanation.

- **[Account / line, department]: [$ variance] ([% variance]) [favorable/unfavorable].**
  - Driver: [commentary from department lead or finance].
  - YTD context: [is this period an outlier or part of a trend?].
  - Outlook: [will this normalize, continue, or accelerate?].

If a line exceeds the threshold but no commentary is available by distribution time, flag explicitly: *"[Commentary pending — target [date]]."*

### Departmental excerpts

Each department lead receives the relevant department's section as a standalone excerpt. Excerpts contain: their lines, their variance commentary, and a one-line summary from the Controller.

### Methodology / sources

- Period covered: 2026-05-25 through 2026-05-25.
- Accrual basis unless explicitly noted.
- Budget version: [e.g., "approved annual operating plan, locked [YYYY-MM-DD]"].
- Reclassifications or non-routine treatments: [noted with explanation].
- Cost allocations: [describe methodology if applicable, or "no allocations applied"].

---
- **Maintainer of this spec:** Controller
- **Last reviewed:** 2026-05-25
- **Cadence:** Monthly
