# NovaTech Data Verification Log

**Project:** NovaTech Revenue Intelligence Dashboard  
**Student:** Kasmya Bhatia  
**Platform:** Amazon QuickSight / Quick Suite  
**Environment:** UdacityQuicksightLab, us-west-2  
**Date:** September 2026

---

## Purpose

This verification log documents the checks performed to ensure that important
dashboard and Amazon Q results agree with the underlying NovaTech source data.

The verification process uses three sources of evidence where applicable:

1. Source CSV / ground-truth calculation
2. Amazon QuickSight Q&A response
3. Final dashboard visual or KPI

The purpose is to ensure that reported business numbers are not based only on
an Amazon Q response or a potentially duplicated joined dataset.

---

## Verification Log

| # | Knowledge Base / Dataset | Question Asked | Expected Answer | Q Answer | Dashboard / Source Check | Match? | Notes |
|---|---|---|---|---|---|---|---|
| 1 | NovaTech CRM Deals | What is the total revenue from closed-won deals in the CRM dataset? | **$707,201** across 315 won deals | **$707,201 across 315 won deals** | Sales Pipeline KPI = **$707,201** | PASS | Exact match |
| 2 | NovaTech CRM Deals | How many unique account IDs are present in the CRM dataset? | **85 unique accounts** | **85 unique account IDs** | Source-level calculation confirms 85 | PASS | Exact match |
| 3 | NovaTech Marketing Campaigns | How many leads responded positively and what is the overall response rate? | **609 / 2,240 = 27.2%** | **609 positive responses; 27.19%** | Source calculation confirms 609 / 2,240 | PASS | Difference is rounding only |
| 4 | NovaTech Marketing Campaigns | What is the earliest and latest campaign date? | **2023-01-01 to 2025-01-31** | **January 1, 2023 to January 31, 2025** | Source date range confirms result | PASS | Exact match |
| 5 | NovaTech Support Tickets | How many tickets have no resolved date? | **59 unresolved tickets** | **59** | Source calculation confirms 59 null resolution dates | PASS | Exact match |
| 6 | NovaTech Support Tickets | How many tickets are in each priority level? | Low 1,500; Medium 1,050; High 400; Critical 50 | Same distribution | Total = **3,000 tickets** | PASS | Exact match |
| 7 | CRM / Dashboard | What is the overall win rate? | **315 / 499 = 63.1%** | **63.1%** | Sales Pipeline KPI = **63.1%** | PASS | Source and dashboard agree |
| 8 | Marketing | What is the total campaign spend? | **$12,359,497.34** | **$12,359,497.34** | Marketing Funnel KPI / source check | PASS | Exact match |
| 9 | Marketing | What is the total attributed revenue? | **Approximately $1.13M** | **Approximately $1.13M** | Marketing Funnel | PASS | Rounded display value |
| 10 | Support / Customer Health | Which account has the highest support-ticket volume? | **ACCT-041 / YieldMax Software** | **ACCT-041 / YieldMax Software** | Customer Health | PASS | 334 tickets |
| 11 | Support / Customer Health | How many tickets remain unresolved? | **59** | **59** | Source calculation | PASS | Joined-model totals must not be used |
| 12 | Marketing | Are the six campaign programs profitable? | **No; all six have negative ROI** | All six negative | Marketing Funnel | PASS | Source and dashboard agree |

---

## Important Grain Verification

The three source datasets contain different levels of detail:

- CRM deals: **499 rows**
- Marketing campaigns: **2,240 rows**
- Support tickets: **3,000 rows**

The unified model is created using:

```text
CRM
  LEFT JOIN Marketing
      ON account_id
          LEFT JOIN Support
              ON account_id
