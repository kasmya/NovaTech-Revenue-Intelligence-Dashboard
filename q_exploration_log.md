# NovaTech Q Exploration Log

**Project:** NovaTech Revenue Intelligence Dashboard  
**Student:** Kasmya Bhatia  
**Platform:** Amazon QuickSight / Quick Suite  
**Q&A Topic:** NovaTech Revenue Intelligence  

---

## Purpose
Amazon Q was used to explore the NovaTech CRM, Marketing, Support and unified datasets using natural-language questions.  

The purpose of this exploration was to determine whether Amazon Q could answer useful business questions and whether those answers were consistent with the dashboard and underlying data.  

Amazon Q results were not automatically treated as ground truth. Important answers were cross-checked against the appropriate dashboard visual or source-level calculation.  

This was particularly important because the unified dataset contains repeated records as a result of joining datasets at the account level.  

---

# Q1 — Highest-Converting Marketing Channel

**Question:** Which campaign channel has the highest conversion rate?  

- **Amazon Q Result:** Direct Mail ≈ 53% conversion rate  
- **Dashboard Check:** Marketing Funnel identifies Direct Mail as strongest channel  
- **Source Check:** Source-level marketing data confirms same conclusion  
- **Result:** PASS  

**Interpretation:** Direct Mail is the strongest-performing channel by measured response rate.  

---

# Q2 — Average Deal Size by Company Size

**Question:** What is the average deal size by company size?  

- **Amazon Q Result:** Enterprise identified as highest average deal size, but values differ from CRM calculation  
- **Investigation:**  
  - CRM dataset = 499 deals  
  - Unified dataset = ~63,420 rows (fan-out effect)  
  - Joined dataset repeats CRM deals across multiple rows  
- **Source Check:** CRM-level calculation produces different averages  
- **Result:** PARTIAL — Grain issue identified  

**Interpretation:** Not a hallucination. Shows importance of dataset grain. Deal-level metrics should be calculated from CRM source, not unified dataset.  

---

# Q3 — Critical vs. Low-Priority Resolution Time

**Question:** What is the average resolution time for critical vs. low-priority support tickets?  

- **Amazon Q Result:**  
  - Critical ≈ 2.36 days  
  - Low ≈ 2.48 days  
- **Dashboard Check:** Customer Health shows similar relationship  
- **Source Check:** Support dataset confirms values  
- **Result:** PASS  

**Interpretation:** Critical and low-priority tickets have similar resolution times.  

---

# Q4 — Accounts With Highest Support-Ticket Volume

**Question:** What are the top accounts by support-ticket volume and associated deal revenue?  

- **Amazon Q Result:** ACCT-041 / YieldMax Software  
  - ≈ 334 support tickets  
  - ≈ $40,722 associated revenue  
- **Dashboard Check:** Customer Health identifies ACCT-041  
- **Source Check:** Support dataset confirms ticket volume  
- **Result:** PASS  

**Interpretation:** Unified dataset is appropriate for account-level analysis. ACCT-041 warrants customer-success attention.  

---

# Q5 — Campaigns Where Spending Exceeds Revenue

**Question:** Are there campaigns where spending exceeds revenue?  

- **Amazon Q Result:** All six campaign programs have negative ROI (~ -83.7% to -97.7%)  
- **Dashboard Check:** Marketing Funnel shows spend > attributed revenue  
- **Source Check:** Marketing dataset confirms negative ROI  
- **Result:** PASS  

**Interpretation:** Campaign programs are not profitable. Marketing allocation should be reviewed.  

---

## Q Exploration Summary

| Question                          | Result  | Main Finding                           |
| --------------------------------- | ------- | -------------------------------------- |
| Highest-converting channel        | PASS    | Direct Mail ≈ 53%                      |
| Average deal size by company size | PARTIAL | Grain issue in joined dataset           |
| Critical vs. low resolution time  | PASS    | Critical ≈ 2.36 days; Low ≈ 2.48 days  |
| Highest support-ticket accounts   | PASS    | ACCT-041 has ≈ 334 tickets             |
| Campaign spending vs. revenue     | PASS    | All six programs have negative ROI     |

---

## Important Finding — Dataset Grain
- Unified dataset created by joining: **CRM → Marketing → Support** using `account_id`  
- Accounts with multiple records cause repeated combinations  
- Unified dataset ≈ 63,420 rows vs. CRM source ≈ 499 deals  
- Metrics like **SUM(deal_value)** should not be calculated over unified dataset  
- Same principle applies to marketing spend and other source-level aggregates  

---

## Q&A Usage Rule
Amazon Q was used primarily for **exploration and question discovery**.  

Verification process:  
**Source Data → Independent Calculation → Amazon Q → Dashboard**  

- If Q result agreed with source and dashboard → **PASS**  
- If discrepancy due to dataset grain → documented, not hidden  

---

## Conclusion
Amazon Q provides useful natural-language access to NovaTech datasets.  

- 4 of 5 representative questions consistent with dashboard and source analysis  
- Average deal-size question exposed dataset-grain issue  
- CRM-level metrics must be calculated from CRM dataset, not unified model  
