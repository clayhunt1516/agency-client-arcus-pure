# Weekly Cash Flow Report

> **Purpose:** Give leadership a current cash position and a near-term outlook so payment decisions, collection efforts, and any funding actions can be made with current information.

## Spec

- **Audience:** Owner / CEO, CFO, Controller. AP specialist for payment prioritization input.
- **Cadence:** Weekly, every [discovery] morning.
- **Owner:** Controller (or designee).
- **Reviewer / approver:** None routinely; CFO consulted if any week shows concern.
- **Source data:**
  - Current bank balances (all material accounts): pulled fresh from [discovery].
  - AR aging snapshot: `/01-accounting/data/ar-aging-2026-05-25.csv`
  - AP open invoices and payment list: from QuickBooks Online AP module.
  - Payroll calendar and amounts: `/01-accounting/data/payroll-calendar-[YYYY].csv` or [discovery].
  - Known recurring debits (rent, debt service, subscriptions): [discovery].
- **Produced by SOP:** `/01-accounting/sops/weekly-cash-flow-review.md` (when this SOP exists).
- **Output location:** `/01-accounting/reports/instances/cash-flow-2026-05-25.md`
- **Distribution:** Email to Controller, CFO, owner. Post in [discovery].

## Structure

### Headline

One paragraph: current cash position, week-over-week direction, any concerns. Lead with the number that matters most to Arcus Pure (typically: total cash across operating accounts).

### Current position

| Account | Balance | As of |
|---|---|---|
| [Operating account] | [$ balance] | [date] |
| [Payroll account] | | |
| [Reserve / savings] | | |
| **Total** | | |

### Inflows expected this week

| Source | Amount | Confidence | Expected date |
|---|---|---|---|
| AR collections | | high/med/low | |
| Customer deposits | | | |
| Other | | | |
| **Total expected** | | | |

Confidence reflects collection certainty. AR over 60 days defaults to "low."

### Outflows expected this week

| Category | Amount | Date |
|---|---|---|
| AP payment run | | [discovery] |
| Payroll | | [discovery] |
| Debt service | | |
| Recurring debits | | |
| Other | | |
| **Total expected** | | |

### Projected end-of-week position

Current position + expected inflows − expected outflows = [$ projected].

If any expected outflow exceeds expected inflows + current position, flag it here with a recommendation (defer payment, accelerate collection, draw from reserves).

### 4-week forward look

| Week ending | Projected open | Inflows | Outflows | Projected close |
|---|---|---|---|---|
| [Week 1 end] | | | | |
| [Week 2 end] | | | | |
| [Week 3 end] | | | | |
| [Week 4 end] | | | | |

Forward weeks rely on standing recurring obligations and AR aging projection. One-time inflows/outflows should be added explicitly with a note.

### Concerns and actions

Items requiring action — collection escalation, payment deferral decisions, line-of-credit draws, etc. Each with owner and target date.

### Methodology / sources

- Bank balance pull date and time: [datetime].
- AR projection method: [e.g., "current and 30-day buckets assumed paid in next 7 days; 60+ day balances excluded from projection."]
- Forward-look assumptions: standing recurring + AR aging projection; does NOT include one-off transactions unless explicitly noted.

---
- **Maintainer of this spec:** Controller
- **Last reviewed:** 2026-05-25
- **Cadence:** Weekly
