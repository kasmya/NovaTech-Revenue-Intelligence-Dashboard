# NovaTech Revenue Intelligence Dashboard
## Udacity — Future AWS Agentic AI Business Professional
**Student:** Kasmya Bhatia
**Submitted:** September 12, 2026  
**Platform:** Amazon QuickSight (SPICE)

---

## 🔗 Live Dashboard Link
[NovaTech Revenue Intelligence Dashboard](https://us-west-2.quicksight.aws.amazon.com/sn/account/UdacityQuicksightLab/accounts/548602084193/dashboards/d14515fc-5eaf-450b-959b-96d3f335a496)

---

## 📁 Folder Structure

```
└── screenshots/
    ├── 01  (Chat with 4 datasets selected as context)
    ├── 02  (BEFORE Topic — 3 questions: Won=315, Spend=$12.36M, Priority=Low)
    ├── 03  (Topic "NovaTech Revenue Intelligence" — 4 datasets + priority answer)
    ├── 04  (AFTER Topic Q1 — "How many CRM deals were Won?" → 315)
    ├── 05  (AFTER Topic Q2 — "Total marketing campaign spend?" → $12,359,497.34)
    ├── 06  (AFTER Topic Q3 — "Which priority has most tickets?" → Low: 1,500)
    ├── 07  (Publish dashboard dialog — name set, All sheets selected)
    ├── 08  (Analyses page — NovaTech CRM Deal Performance Dashboard listed)
    ├── 09  (Add Quick assets — 4 datasets, novatech_crm_deals checked)
    ├── 10  (Verification — CRM rows = 499)
    ├── 11  (Verification — CRM rows=499 + date range Dec 2023 to Jan 2025)
    ├── 12  (Verification — date range + annual_income belongs to marketing)
    ├── 13  (Verification — annual_income null + 6 distinct campaign names)
    ├── 14  (Data type fix — marketing: campaign_date → Date, annual_income → Decimal)
    ├── 15  (Data type fix — CRM: deal_created_date → Date, deal_value → Decimal)
    ├── 16  (Data type fix — support: ticket_resolved_date → Date yyyy-MM-dd HH:mm:ss)
    ├── 17  (Join 1 config — Left join, CRM + Marketing on account_id = account_id)
    ├── 18  (Calculated fields — Is Won + Sales Cycle Duration with formulas)
    ├── 19  (All 4 datasets in SPICE owned by Me)
    ├── 20  (Full join diagram — all 3 CSVs → Join1 → Join2 → 2 calculated fields)
    ├── 21  (Calculated field — Net Marketing Profit = revenue_attributed - campaign_spend)
    ├── 22  (Join 2 config — Left join, Join1 + support tickets on account_id.1 = account_id)
    └── 23  (CRM pipeline diagram + Is Won = ifelse(deal_stage='Won',1,0))
```
---

## 📊 Project Summary

**Goal:** Unify NovaTech's siloed CRM, Marketing, and Support data into a single Revenue Intelligence Dashboard so the revenue team can stop pulling manual reports every Monday.

### Data Sources
| Dataset | Rows | Key Field |
|---|---|---|
| novatech_crm_deals.csv | 499 | account_id |
| novatech_marketing_campaigns.csv | 2,240 | account_id |
| novatech_support_tickets.csv | 3,000 | account_id |
| novatech_unified (joined) | >499 | account_id |

### Dashboard Sheets
| Sheet | Dataset | Key Insight |
|---|---|---|
| Marketing Funnel | Marketing | All 6 campaigns negative ROI; Direct Mail converts at 53% |
| Sales Pipeline | CRM | 63.1% win rate; $707,201 total won revenue |
| Customer Health | Unified | ACCT-041 highest risk: 334 tickets + $40,722 revenue |

### Key Findings
- 💸 Total marketing spend: **$12.36M** vs **$1.13M** revenue attributed (−90.9% ROI)
- ✅ Win rate: **63.1%** (315 won / 184 lost)
- 🚨 ACCT-041: highest revenue account AND most support tickets
- ⚠️ Critical tickets resolve in same time as low-priority (~58 hrs each)

### Calculated Fields
- **Sales Cycle Duration** = `dateDiff({deal_created_date}, {deal_closed_date}, 'DD')`
- **Is Won** = `ifelse({deal_stage}='Won', 1, 0)`
- **Net Marketing Profit** = `{revenue_attributed} - {campaign_spend}`

### Join Configuration
- Anchor: CRM deals
- Join 1: CRM **LEFT JOIN** Marketing on `account_id`
- Join 2: Result **LEFT JOIN** Support on `account_id`

---

## 📋 Rubric Checklist

- ✅ Verification log — 7 entries across all 3 knowledge bases
- ✅ Data type corrections — ticket_resolved_date, campaign_date, deal dates
- ✅ Calculated fields — Sales Cycle Duration, Is Won, Net Marketing Profit
- ✅ Unified dataset — LEFT JOIN all 3 sources on account_id
- ✅ 3 dashboard sheets — Marketing Funnel, Sales Pipeline, Customer Health
- ✅ KPI cards on every sheet
- ✅ Filters on every sheet
- ✅ One-click filtering action
- ✅ Cross-sheet navigation
- ✅ Dashboard published and PDF exported
- ✅ Before/after Topic screenshots
- ✅ Q Exploration Log — 5 entries across all 3 domains
- ✅ 5 dashboard annotations with numbers + implications + actions
- ✅ Written report for Sarah Chen — 3 pages

---

*Built with Amazon QuickSight SPICE | Udacity AWS AI & ML Scholars Program*
