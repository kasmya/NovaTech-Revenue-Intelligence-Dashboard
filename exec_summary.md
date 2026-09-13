# Executive Summary

## Purpose

The NovaTech Revenue Intelligence dashboard consolidates CRM, marketing, and customer-support data into a single Amazon QuickSight dashboard for executive analysis.

The dashboard contains three sheets:

1. **Sales Pipeline** — CRM performance and deal outcomes
2. **Marketing Funnel** — campaign response and marketing efficiency
3. **Customer Health** — customer support activity and sentiment

---

## Sales Pipeline

The CRM dataset contains **499 deals**.

### Key findings

- **315 deals were won** and **184 were lost**.
- Overall win rate: **63.1%**.
- Total closed-won revenue: **$707,201**.
- The **Central** region generated the highest closed-won revenue at approximately **$274,285**.
- Central also had the strongest regional win rate at approximately **69.9%**.

The sales analysis provides visibility into deal outcomes, revenue contribution, regional performance, and sales-cycle behavior.

---

## Marketing Funnel

The marketing dataset contains **2,240 campaign records**.

### Key findings

- **609 of 2,240** records generated a positive response.
- Overall response rate: approximately **27.2%**.
- Total campaign spend is approximately **$12.36M**.
- Revenue attributed to marketing is approximately **$1.13M**.
- The resulting blended marketing ROI is approximately **-90.9%**.

All six major campaign programs show negative ROI, indicating that the current marketing mix requires review.

**Direct Mail** produced the strongest response rate at approximately **53%**, while still showing negative financial ROI.

The weakest ROI values were observed for **Organic Search** and **Email**, at approximately **-97.8%** and **-94.9%**, respectively.

---

## Customer Health

The customer-support dataset contains **3,000 support tickets**.

The analysis identifies differences in ticket volume, customer sentiment, priority, and resolution performance.

### Key findings

- **ACCT-041 (YieldMax)** has the highest support-ticket volume, with **334 tickets**.
- The account is associated with approximately **$40,722** in income.
- **59 tickets** have missing customer-sentiment values.
- Negative customer sentiment accounts for **684** records in the source support data.
- Critical tickets do not show a substantially faster resolution time than low-priority tickets.

The Customer Health sheet therefore highlights accounts that may require closer operational or customer-success attention.

---

## Important Data Modeling Note

The unified dataset is created by joining the CRM, marketing, and support datasets using `account_id`.

Because the source datasets have different levels of detail, joining them can create **row multiplication (fan-out)**. Consequently, aggregated sums from the unified dataset can be inflated.

For this reason:

- **CRM KPIs** are calculated from the CRM source dataset.
- **Marketing KPIs** are calculated from the marketing source dataset.
- **Support KPIs** are calculated from the support source dataset.
- The **unified dataset** is primarily used for cross-domain analysis and Q&A where appropriate.

This distinction is important when interpreting dashboard totals.

---

## Data Quality Observations

The source data contains several quality issues identified during validation:

- **3 duplicate `opportunity_id` values** in the CRM data.
- **4 duplicate `ticket_id` values** in the support data.
- **59 missing customer-sentiment values**.
- Some marketing and support records reference accounts that do not appear in the CRM dataset.

These observations were retained as part of the analysis rather than silently removed.

---

## Executive Recommendations

### 1. Review marketing allocation

The negative ROI across the campaign programs indicates a need to reassess marketing spending and channel allocation.

### 2. Investigate high-support accounts

Accounts with unusually high ticket volumes, particularly **ACCT-041**, should be investigated for recurring product, service, or customer-experience issues.

### 3. Investigate sales losses

The CRM data should be examined further to understand the primary reasons for lost opportunities and identify opportunities to improve the win rate.

### 4. Monitor critical support tickets

Critical tickets should receive additional operational attention because their resolution performance is not substantially better than lower-priority tickets.

---

## Validation

Key dashboard values were checked against the underlying source datasets and QuickSight analysis/Q&A results.

The supporting validation artifacts include:

- `verification_log.md`
- `q_exploration_log.md`
- `methodology.md`

The verification process was used to distinguish reliable source-level KPI calculations from values affected by the unified dataset's row-grain behavior.

---

## Conclusion

The NovaTech dashboard provides a unified executive view of **sales performance, marketing effectiveness, and customer health**.

The strongest immediate findings are:

- **63.1% CRM win rate**
- **$707,201 closed-won revenue**
- **27.2% marketing response rate**
- **-90.9% blended marketing ROI**
- **334 support tickets for ACCT-041**

The dashboard should be used together with the documented validation and data-modeling notes when interpreting aggregated metrics.
