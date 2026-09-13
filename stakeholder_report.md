# NovaTech Revenue Intelligence Report

## Prepared for: Sarah Chen, VP Sales & Marketing

---

## Executive Overview

The NovaTech Revenue Intelligence dashboard provides a consolidated view of sales performance, marketing effectiveness, and customer health using CRM, marketing campaign, and support-ticket data.

The analysis identifies three major areas requiring management attention:

1. **Sales performance** is relatively strong, with a 63.1% win rate and $707,201 in closed-won revenue.
2. **Marketing efficiency is weak**, with approximately $12.36M in campaign spending against approximately $1.13M in attributed revenue.
3. **Customer-support activity is concentrated among several accounts**, with ACCT-041 showing particularly high ticket volume.

---

## 1. Sales Performance

The CRM dataset contains **499 deals**.

### Key results

- **315 won deals**
- **184 lost deals**
- **63.1% overall win rate**
- **$707,201 closed-won revenue**

Regional performance shows that the **Central region** generated the highest closed-won revenue, contributing approximately **$274,285**.

Central also recorded the strongest regional win rate at approximately **69.9%**.

### Recommendation

Management should examine the characteristics of successful Central-region deals and determine whether the same sales practices can be applied to weaker-performing regions.

Lost opportunities should also be reviewed by loss reason to identify recurring barriers to conversion.

---

## 2. Marketing Performance

The marketing dataset contains **2,240 campaign records**.

The analysis identified:

- **609 positive responses**
- Approximately **27.2% response rate**
- Approximately **$12.36M campaign spend**
- Approximately **$1.13M attributed revenue**
- Approximately **-90.9% blended ROI**

All six major campaign programs show negative ROI.

### Channel observations

**Direct Mail** produced the strongest response rate at approximately **53%**, although its financial ROI remained negative at approximately **-70.7%**.

The weakest ROI results were observed for:

- **Organic Search: approximately -97.8%**
- **Email: approximately -94.9%**

### Recommendation

Marketing expenditure should be reviewed at both the program and channel level.

High-response channels should not automatically be interpreted as financially successful. Response volume and financial return should be evaluated together before reallocating budget.

---

## 3. Customer Health

The support dataset contains **3,000 support tickets**.

One of the most notable findings is the concentration of support activity around **ACCT-041 (YieldMax)**.

### ACCT-041

- **334 support tickets**
- Approximately **$40,722 associated income**
- **59 open tickets** identified in the analysis

This level of support activity makes the account a priority for further investigation.

### Customer sentiment

The source support data contains:

- **684 negative sentiment records**
- **304 positive sentiment records**
- **1,953 neutral sentiment records**
- **59 records with missing sentiment**

The missing sentiment values should be considered when interpreting sentiment distributions.

### Recommendation

Customer-success and support teams should investigate high-ticket-volume accounts to determine whether recurring product or service issues are contributing to support demand.

---

## 4. Support Resolution Performance

The analysis also compares resolution performance across ticket priorities.

Critical tickets do not demonstrate substantially faster resolution than low-priority tickets. The observed resolution times are approximately **2.36 days for critical tickets** and **2.48 days for low-priority tickets**.

This suggests that ticket priority is not currently associated with a large difference in resolution time.

### Recommendation

Management should review the operational workflow for critical tickets, including escalation procedures, assignment, and response capacity.

---

## 5. Priority Actions

### Action 1 — Reassess marketing spending

The negative ROI across all major campaign programs warrants a review of current marketing allocation.

### Action 2 — Investigate high-support accounts

ACCT-041 and other high-ticket-volume accounts should be examined for recurring issues and customer-experience risks.

### Action 3 — Analyze lost opportunities

The sales team should examine loss reasons and identify patterns that could improve the current **63.1% win rate**.

### Action 4 — Review critical-ticket handling

The similarity between critical and low-priority resolution times suggests an opportunity to improve escalation and resolution processes.

---

## 6. Data and Modeling Considerations

The dashboard combines CRM, marketing, and support information through account-level joins.

Because these datasets operate at different levels of detail, the unified dataset can produce **row multiplication (fan-out)** when multiple records from different source datasets correspond to the same account.

Therefore, source-specific datasets are used for authoritative aggregate KPIs such as:

- CRM revenue
- CRM win rate
- Marketing spend
- Marketing attributed revenue
- Support-ticket counts

The unified dataset is used primarily for cross-domain exploration and Q&A.

This distinction prevents inflated joined-row totals from being interpreted as source-level business metrics.

---

## 7. Dashboard Usage

The dashboard consists of three sheets:

### Sales Pipeline

Used to analyze:

- Deal outcomes
- Won revenue
- Win rate
- Regional performance
- Sales-cycle behavior

### Marketing Funnel

Used to analyze:

- Campaign responses
- Channel performance
- Marketing spend
- Attributed revenue
- ROI

### Customer Health

Used to analyze:

- Support-ticket volume
- Customer sentiment
- Ticket priority
- Resolution performance
- High-risk/high-volume accounts

Filters and cross-sheet navigation allow users to move from overall performance to more detailed account or category-level analysis.

---

## 8. Final Management Summary

The dashboard indicates that NovaTech has a comparatively strong sales conversion rate but significant opportunities to improve marketing efficiency and customer-support operations.

The most important findings for management are:

| Area | Finding |
|---|---|
| Sales | **63.1% win rate** |
| Won revenue | **$707,201** |
| Marketing response | **27.2%** |
| Marketing spend | **$12.36M** |
| Attributed revenue | **$1.13M** |
| Blended marketing ROI | **-90.9%** |
| Highest-support account | **ACCT-041 / YieldMax** |
| Tickets for ACCT-041 | **334** |

The recommended priority is to **review marketing allocation, investigate high-support accounts, analyze sales losses, and improve escalation of critical support tickets**.

---

## Validation Note

The reported KPI values were checked against the underlying source data and QuickSight analyses.

Supporting documentation is provided in:

- `verification_log.md`
- `q_exploration_log.md`
- `methodology.md`
- `exec_summary.md`

These files document the validation process and the handling of the unified dataset's row-grain limitations.
