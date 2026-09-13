# NovaTech Data Verification Log

**Project:** NovaTech Revenue Intelligence Dashboard  
**Student:** Kasmya Bhatia  
**Platform:** Amazon QuickSight / Quick Suite  
**Date:** September 2026  

---

## Purpose
This verification log documents the checks performed to ensure that important dashboard and Amazon Q results agree with the underlying NovaTech source data.  

The verification process uses three sources of evidence where applicable:
- Source CSV / ground-truth calculation  
- Amazon Q response  
- Final dashboard visual or KPI  

The purpose is to ensure that reported business numbers are not based only on an Amazon Q response or a potentially duplicated joined dataset.

---

## Verification Log

### 1. CRM — Total Closed-Won Revenue
- **Question:** What is the total revenue from closed-won deals in the CRM dataset?  
- **Expected answer:** $707,201 across 315 won deals.  
- **Amazon Q answer:** $707,201 across 315 won deals.  
- **Dashboard check:** The Sales Pipeline dashboard reports $707,201 in won revenue.  
- **Result:** PASS  
- **Notes:** The Q result, source-level result and dashboard KPI agree.  

---

### 2. CRM — Unique Accounts
- **Question:** How many unique account IDs are present in the CRM dataset?  
- **Expected answer:** 85 unique account IDs.  
- **Amazon Q answer:** 85 unique account IDs.  
- **Source check:** The CRM source data confirms 85 unique accounts.  
- **Result:** PASS  
- **Notes:** The result agrees with the source data.  

---

### 3. Marketing — Positive Responses
- **Question:** How many marketing records received a positive response and what is the overall response rate?  
- **Expected answer:** 609 positive responses out of 2,240 records (~27.2%).  
- **Amazon Q answer:** 609 positive responses and ~27.2%.  
- **Source check:** 609 / 2,240 = ~27.2%.  
- **Result:** PASS  
- **Notes:** Any small difference is due to display rounding.  

---

### 4. Marketing — Date Range
- **Question:** What is the date range of the marketing dataset?  
- **Expected answer:** Jan 1, 2023 to Jan 31, 2025.  
- **Amazon Q answer:** Jan 1, 2023 to Jan 31, 2025.  
- **Source check:** The source data confirms the same date range.  
- **Result:** PASS  

---

### 5. Support — Unresolved Tickets
- **Question:** How many support tickets have no resolved date?  
- **Expected answer:** 59 unresolved tickets.  
- **Amazon Q answer:** 59 unresolved tickets.  
- **Source check:** The Support dataset contains 59 records with missing resolution date.  
- **Result:** PASS  

---

### 6. Support — Priority Distribution
- **Question:** How many support tickets are in each priority level?  
- **Expected answer:**  
  - Low: 1,500  
  - Medium: 1,050  
  - High: 400  
  - Critical: 50  
- **Amazon Q answer:** Same distribution.  
- **Source check:** Totals 3,000 support tickets.  
- **Result:** PASS  

---

### 7. CRM — Win Rate
- **Question:** What is the overall sales win rate?  
- **Expected answer:** 315 won deals out of 499 (63.1%).  
- **Amazon Q answer:** 63.1%.  
- **Dashboard check:** Sales Pipeline dashboard reports 63.1%.  
- **Result:** PASS  

---

### 8. Marketing — Campaign Spend
- **Question:** What is the total marketing campaign spend?  
- **Expected answer:** ~$12.36 million.  
- **Amazon Q / source result:** ~$12.36 million.  
- **Dashboard check:** Marketing Funnel reports ~$12.36 million.  
- **Result:** PASS  
- **Notes:** Dashboard display may round the exact source value.  

---

### 9. Marketing — Attributed Revenue
- **Question:** What is the total revenue attributed to marketing campaigns?  
- **Expected answer:** ~$1.13 million.  
- **Amazon Q / source result:** ~$1.13 million.  
- **Dashboard check:** Marketing Funnel reports ~$1.13 million.  
- **Result:** PASS  

---

### 10. Customer Health — Highest Ticket Volume
- **Question:** Which account has the highest support-ticket volume?  
- **Expected answer:** ACCT-041 / YieldMax Software.  
- **Amazon Q answer:** ACCT-041 / YieldMax Software.  
- **Dashboard check:** Customer Health identifies ACCT-041.  
- **Result:** PASS  
- **Additional info:** ACCT-041 has ~334 support tickets and ~$40,722 in associated revenue.  

---

### 11. Support — Unresolved Ticket Count
- **Question:** How many support tickets remain unresolved?  
- **Expected answer:** 59.  
- **Amazon Q answer:** 59.  
- **Source check:** 59 records missing resolution date.  
- **Result:** PASS  

---

### 12. Marketing — Campaign Profitability
- **Question:** Are the campaign programs profitable?  
- **Expected answer:** All six programs have negative ROI.  
- **Amazon Q answer:** All six programs have negative ROI.  
- **Dashboard check:** Marketing Funnel shows spend > attributed revenue.  
- **Result:** PASS  

---

## Join and Data-Grain Verification
- CRM is deal-oriented, Marketing is campaign/lead-oriented, Support is ticket-oriented.  
- Datasets combined using **account ID**:  
  - CRM → LEFT JOIN Marketing → LEFT JOIN Support  
- Unified dataset produces ~63,420 rows due to fan-out effect.  
- **Implication:** Direct summing of CRM revenue in unified dataset inflates values.  
- **Strategy:**  
  - CRM source → revenue, deal counts, win rate  
  - Marketing source → spend, attributed revenue, ROI  
  - Unified dataset → account-level analysis, support relationships, customer health  

---

## Data Quality Verification
- **Duplicate Opportunity IDs:** 3 identified, documented.  
- **Duplicate Ticket IDs:** 4 identified, documented.  
- **Missing Customer Sentiment:** 59 support records missing values.  
- **Orphan Accounts:** Marketing/Support contain accounts not in CRM. Preserved via LEFT JOIN.  
- **Data-Type Corrections:** Numeric/date fields corrected in QuickSight.  

---

## Verification Principle
Sequence followed:  
**Source Data → Independent Calculation → Amazon Q → Dashboard**  

- A result is verified when all three agree (allowing rounding).  
- Discrepancies due to join grain are documented, not hidden.  
- Amazon Q is treated as an **exploration tool**, not sole source of truth.  
- Final stakeholder-facing numbers come from source datasets, verified against dashboard.  
