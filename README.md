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
NovaTech_Final/
├── README.md                        ← this file
│
├── documents/
│   └── novatech_documentation.pdf  ← verification log, Q log, report, annotations
│
├── pdfs/
│   ├── Marketing_Funnel.pdf         ← Sheet 1 export
│   ├── Sales_Pipeline.pdf           ← Sheet 2 export
│   ├── Customer_Health.pdf          ← Sheet 3 export
│   └── Executive_Summary.pdf        ← Full dashboard export
│
└── screenshots/
    ├── 01_analyses_page.png
    ├── 02_datasets_all_four_SPICE.png
    ├── 03_verification_chat_datasets_selected.png
    ├── 04_before_topic_all3_questions.png         ← BEFORE Topic baseline
    ├── 05_topic_config_all4_datasets.png          ← Topic configuration
    ├── 06_after_topic_q1_won_deals.png            ← AFTER Topic Q1
    ├── 07_after_topic_q2_campaign_spend.png       ← AFTER Topic Q2
    ├── 08_after_topic_q3_priority.png             ← AFTER Topic Q3
    ├── 09_publish_dashboard.png
    ├── 10_quicksight_home.png
    ├── 11_datasets_SPICE_confirmed.png
    ├── 12_verification_datasets_with_chat.png
    ├── 13_verification_dataset_selector.png
    ├── 14_verification_crm_rows_499.png           ← Verification Q1
    ├── 15_verification_crm_date_range.png         ← Verification Q2
    ├── 16_verification_null_annual_income.png     ← Verification Q3
    ├── 17_verification_campaign_names_6.png       ← Verification Q4
    ├── 18_datatype_fix_ticket_resolved_datetime.png
    ├── 19_datatype_marketing_campaigns.png        ← Data type fix
    ├── 20_datatype_crm_deals.png                  ← Data type fix
    ├── 21_datatype_support_tickets_datetime.png   ← Data type fix (key)
    ├── 22_join1_crm_marketing_config.png          ← Join 1 config
    ├── 23_calculated_fields_sales_cycle_iswon.png ← Calculated fields
    ├── 24_all_datasets_SPICE_owned.png            ← All 4 datasets
    ├── 25_join_diagram_all3_unified.png           ← Join diagram (key)
    ├── 26_calculated_field_net_marketing_profit.png
    ├── 27_join2_support_tickets_config.png        ← Join 2 config
    └── 28_calculated_field_iswon.png
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
