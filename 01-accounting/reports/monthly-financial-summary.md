# Monthly Financial Summary

> **Purpose:** Give Arcus Pure's leadership a single document each month summarizing financial performance, explaining material variances, and surfacing items that need attention.

## Spec

- **Audience:** Owner / CEO, CFO/Controller, department heads (department highlights only).
- **Cadence:** Monthly, distributed within [discovery] of month-end close.
- **Owner:** Controller (production), with input from department leads on variance commentary.
- **Reviewer / approver:** CFO or owner before distribution.
- **Source data:**
  - GL export for the closed period: `/01-accounting/data/gl-export-[YYYY-MM].csv`
  - Budget for the period: `/06-executive/data/budget-[YYYY].csv`
  - AR aging at month-end: `/01-accounting/data/ar-aging-2026-05-25.csv`
  - AP aging at month-end: `/01-accounting/data/ap-aging-2026-05-25.csv`
  - Cash position at month-end: `/01-accounting/data/cash-balance-2026-05-25.csv`
- **Produced by SOP:** `/01-accounting/sops/month-end-close.md` (the close SOP's final step is producing this report).
- **Output location:** `/01-accounting/reports/instances/monthly-financial-summary-[YYYY-MM].md`
- **Distribution:** Email to `leadership@[discovery]` and posted in [discovery].

## Structure

### Headline

One paragraph stating: was the month on plan, ahead, or behind? What's the most important driver? Is anything trending in a direction that needs attention?

Example phrasing: *"October revenue came in $X (Y%) above budget driven by service department, partially offset by lower equipment sales. Operating margin is on plan. Watch item: AR over 90 days has grown for the third consecutive month."*

### Headline figures

| Metric | Actual | Budget | Variance | Prior month | YoY |
|---|---|---|---|---|---|
| Revenue | | | | | |
| Gross margin % | | | | | |
| Operating expense | | | | | |
| Operating income | | | | | |
| Cash position (end of period) | | | | | |

### Department highlights

One or two bullets per operational department deployed by the industry module â€” what stood out, what's worth flagging. Department leads contribute these; Controller compiles.

### Variances over [materiality threshold]

Every line item that varied from budget by more than the materiality threshold gets explained. Format:

- **[Account / line]: [$ variance] ([% variance]) [favorable/unfavorable].** [explanation — cite the specific event or transaction that drove it]

If nothing exceeds the threshold, state that explicitly: *"No line items exceeded the [threshold-low] materiality threshold this period."* Don't omit the section.

### AR / AP health

- Total AR: [$ current] (change vs prior month: [threshold-low])
- AR over 90 days: [$ current] (change: [threshold-low])
- Total AP: [$ current] (change: [threshold-low])
- Notable concentration risks or aging issues: [description, or "none."]

### Open items

Action items surfaced by this report. Each item has an owner, target date, and brief description.

### Methodology / sources

- Period covered: 2026-05-25 through 2026-05-25.
- All figures accrual-basis unless explicitly noted.
- Source files (with export dates) listed in spec above.
- Non-routine treatments (one-time adjustments, accruals, reclasses, prior-period corrections) noted here with explanation.

---
- **Maintainer of this spec:** Controller
- **Last reviewed:** 2026-05-25
- **Cadence:** Monthly
