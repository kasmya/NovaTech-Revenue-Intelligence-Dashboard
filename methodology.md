# NovaTech Revenue Intelligence Dashboard — Methodology

**Project:** NovaTech Revenue Intelligence Dashboard  
**Student:** Kasmya Bhatia  
**Platform:** Amazon QuickSight / Quick Suite  
**Date:** September 2026  

---

## 1. Project Objective
The objective of the NovaTech Revenue Intelligence Dashboard is to combine CRM, Marketing and Support information into a single business intelligence experience.  

The dashboard is designed to help stakeholders understand:
- Sales pipeline performance  
- Marketing funnel performance and efficiency  
- Customer support activity  
- Customer-level health and potential risk  

The final dashboard consists of three analytical sheets:
1. Marketing Funnel  
2. Sales Pipeline  
3. Customer Health  

Amazon Q is additionally used as a natural-language exploration layer over the project data.  

---

## 2. Source Datasets

### CRM Deals
**File:** `novatech_crm_deals.csv`  
**Rows:** 499  

Contains deal-level information for sales pipeline and revenue analysis.  
Key fields: `account_id`, `deal_stage`, `deal_value`, `deal_created_date`, `deal_closed_date`  

---

### Marketing Campaigns
**File:** `novatech_marketing_campaigns.csv`  
**Rows:** 2,240  

Contains campaign and response information for funnel and ROI analysis.  
Key measures: campaign spend, attributed revenue, response info, channel info  

---

### Support Tickets
**File:** `novatech_support_tickets.csv`  
**Rows:** 3,000  

Contains customer support activity for health and service analysis.  
Key fields: `account_id`, ticket priority, resolution info, sentiment, ticket IDs  

---

## 3. Data Preparation
Datasets imported into Amazon QuickSight SPICE. Checked for:
- Correct field names  
- Numeric/date types  
- Missing values  
- Duplicate IDs  
- Relationships  

Configured numeric and date fields appropriately.  

---

## 4. Data Quality Checks
- **CRM:** 3 duplicate opportunity IDs  
- **Support:** 4 duplicate ticket IDs, 59 missing sentiment values  
- **Orphan Accounts:** Marketing/Support contain accounts not in CRM  
- **Source Differences:** Actual source data used when definitions differed  

---

## 5. Unified Data Model
Datasets joined on `account_id`:  
CRM → LEFT JOIN Marketing → LEFT JOIN Support  

CRM is anchor dataset; LEFT JOINs preserve CRM records even without Marketing/Support.  

---

## 6. Join Grain and Fan-Out
Different grains:  
- CRM = deal-level  
- Marketing = campaign/response-level  
- Support = ticket-level  

Fan-out effect: unified dataset ≈ 63,420 rows (vs. 499 CRM deals).  

---

## 7. Aggregation Strategy

### CRM metrics
- Won revenue, deal value, won/lost counts, win rate, pipeline metrics  
- Key result: **$707,201 won revenue across 315 won deals**  

### Marketing metrics
- Campaign spend, attributed revenue, response counts/rates, ROI  
- Key results:  
  - **609 positive responses (~27.2%)**  
  - **$12.36M campaign spend**  
  - **$1.13M attributed revenue**  

### Customer Health metrics
- Unified dataset used for account-level analysis (support volume, sentiment, relationships).  

---

## 8. Important Aggregation Limitation
Unified dataset not a transaction-level fact table.  
Direct SUMs (e.g., `SUM(deal_value)`) inflate results.  

Rule:  
- Sales revenue → CRM source  
- Marketing spend → Marketing source  
- Support analysis → Support/unified dataset  

---

## 9. Calculated Fields
- **Is Won:** `ifelse({deal_stage}='Won', 1, 0)`  
- **Sales Cycle Duration:** `dateDiff({deal_created_date}, {deal_closed_date}, 'DD')`  
- **Net Marketing Profit:** `{revenue_attributed} - {campaign_spend}`  

---

## 10. Dashboard Structure

### Marketing Funnel
Focus: spend, attributed revenue, responses, channel performance, ROI  

### Sales Pipeline
Focus: won revenue, win rate, deal performance, stages  
- Reports: **315 won deals / 499 total**  
- **63.1% win rate**  

### Customer Health
Focus: support activity, priority, resolution, sentiment, account-level analysis  
- Example: **ACCT-041 / YieldMax Software**  
  - ≈ 334 tickets  
  - ≈ $40,722 revenue  

---

## 11. Dashboard Interactivity
Includes filters, visual interactions, cross-sheet navigation, account-level exploration.  

---

## 12. Amazon Q / Q&A Methodology
Used for natural-language exploration.  
Representative questions: conversion rates, deal size, resolution times, support volume, campaign ROI.  
Results verified against source and dashboard.  
Documented in `q_exploration_log.md`.  

---

## 13. Verification Method
Process:  
**Source → Independent Calculation → Amazon Q → Dashboard**  

Stakeholder-facing values accepted only after verification.  
Documented in `verification_log.md`.  

---

## 14. Handling Q&A Discrepancies
Example: average deal size by company size.  
Discrepancy due to dataset grain (fan-out).  
Resolved by using CRM source dataset.  

---

## 15. Dashboard Design Principle
Rule: **Use source dataset whose grain matches the metric.**  
- Deal revenue → CRM  
- Marketing spend → Marketing  
- Ticket volume → Support  
- Customer relationships → Unified  

---

## 16. Final Reporting Principle
Amazon Q = exploration tool, not sole truth.  
Process: **Source → Calculation → Q → Dashboard → Verification**  

---

## 17. Limitations
- Different dataset grains → fan-out  
- Marketing attribution not strictly causal  
- Support data: missing sentiment, duplicate IDs  
- Historical scope limited to supplied period  

---

## 18. Summary
Dashboard uses three source datasets + unified model + source-specific aggregation + Amazon Q exploration.  

Methodology emphasizes:
- Correct data types  
- Source-level verification  
- Proper aggregation grain  
- Transparent join logic  
- Independent metric checks  
- Documented discrepancies  

Final dashboard provides three views:  
**Marketing Funnel → Sales Pipeline → Customer Health**  
with Amazon Q as natural-language exploration layer.  
