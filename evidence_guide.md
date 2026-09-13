# Evidence Guide

## Purpose
This document explains where the main evidence for the NovaTech Revenue Intelligence dashboard can be found.  

The project uses a combination of QuickSight screenshots, source-data checks, Q&A verification, and written documentation to provide an evidence trail for the dashboard.  

---

## 1. Data Source Evidence
Evidence should establish that the three source datasets were successfully uploaded and available in QuickSight.

### CRM
- Expected source size: **499 rows**  
- File: `novatech_crm_deals.csv`  
- Evidence: dataset in QuickSight with available records  

### Marketing
- Expected source size: **2,240 rows**  
- File: `novatech_marketing_campaigns.csv`  
- Evidence: dataset in QuickSight with available records  

### Support
- Expected source size: **3,000 rows**  
- File: `novatech_support_tickets.csv`  
- Evidence: dataset in QuickSight with available records  

---

## 2. Data Type and Field Evidence
Screenshots should show:
- Dataset fields  
- Date fields  
- Numeric fields  
- Categorical fields  
- Corrected field types  

Ensures calculations, filtering, and visuals operate correctly.  

---

## 3. Calculated Field Evidence
The dashboard uses calculated fields:

### Is Won
```text
ifelse({deal_stage}='Won', 1, 0)
```

### Sales Cycle Duration
```text
dateDiff({deal_created_date}, {deal_closed_date}, 'DD')
```

### Net Marketing Profit
```text
{revenue_attributed} - {campaign_spend}
```

Evidence: calculated-field definitions and their use in analysis.  

---

## 4. Unified Dataset Evidence
Unified dataset created by joining on `account_id`:

```text
CRM
  |
  | LEFT JOIN on account_id
  v
Marketing
  |
  | LEFT JOIN on account_id
  v
Support
```

Fan-out effect documented; aggregate values interpreted carefully.  

---

## 5. Dashboard Evidence
Three sheets:

### Sales Pipeline
Evidence: KPI cards, deal-stage analysis, won revenue, win rate, regional performance, sales-cycle analysis, filters.  

### Marketing Funnel
Evidence: responses, channel analysis, spend, attributed revenue, ROI, filters.  

### Customer Health
Evidence: ticket volume, sentiment, priority, resolution, account-level analysis, filters.  

---

## 6. Dashboard Navigation and Interactivity
Evidence: filters applied, visual interactions, one-click filtering, cross-sheet navigation, published dashboard behavior.  

---

## 7. Dashboard Annotations
Evidence: annotations highlighting important findings in published dashboard.  

---

## 8. Q&A Evidence
QuickSight Q&A tested.  

- Main validation: `verification_log.md`  
- Exploratory questions: `q_exploration_log.md`  

Evidence: question, Q&A response, expected result, dashboard comparison, match/discrepancy.  

---

## 9. Q&A Validation
Key checks:

### CRM
- Closed-won revenue  
- Won deals  
- Unique accounts  

### Marketing
- Positive responses  
- Response rate  
- Date range  

### Support
- Missing sentiment/resolution values  
- Priority distribution  
- Ticket counts  

---

## 10. Q&A Limitation Evidence
Limitation: misleading aggregates from unified dataset (e.g., average deal size).  

Documented in `q_exploration_log.md`.  
Dashboard uses source-specific datasets for KPIs.  

---

## 11. Independent Verification
Process:

```text
Raw CSV data
     |
     v
Independent calculation / validation
     |
     v
QuickSight Q&A
     |
     v
Dashboard visual
     |
     v
Verification log
```

---

## 12. Key Numbers to Verify

| Metric                  | Expected value |
| ----------------------- | -------------: |
| CRM records             |            499 |
| Won deals               |            315 |
| Lost deals              |            184 |
| CRM win rate            |          63.1% |
| Closed-won revenue      |       $707,201 |
| Marketing records       |          2,240 |
| Positive responses      |            609 |
| Marketing response rate |          27.2% |
| Support tickets         |          3,000 |
| ACCT-041 tickets        |            334 |
| Marketing spend         |       ~$12.36M |
| Attributed revenue      |        ~$1.13M |
| Blended marketing ROI   |        ~-90.9% |

---

## 13. Stakeholder Report Evidence
File: `stakeholder_report.md`  
Interpreted with verification and methodology docs.  

---

## 14. PDF Evidence
Dashboard exported as PDF:  
`deliverables/pdf/dashboard_export.pdf`  

Check: sheet order, visuals, text readability, KPI visibility, chart placement, no blank pages.  

---

## 15. Evidence Organization
Key supporting files:  

```text
verification_log.md
q_exploration_log.md
methodology.md
exec_summary.md
stakeholder_report.md
evidence_guide.md
```

Together, these document:
- Data validation  
- Q&A testing  
- Data modeling  
- Dashboard methodology  
- Executive findings  
- Stakeholder recommendations  
- Evidence locations  

---

## 16. Evidence Principle
The project follows an evidence-first approach.  

Important dashboard claims should be traceable to:
1. Source data  
2. Independent calculation  
3. QuickSight analysis/Q&A  
4. Dashboard visualization  
5. Documentation  

This makes the dashboard easier to audit, reproduce, and explain.  

---
