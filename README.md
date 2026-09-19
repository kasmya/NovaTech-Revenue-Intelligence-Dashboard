# NovaTech Revenue Intelligence Dashboard

## Udacity — Future AWS Agentic AI Business Professional

---

## 🔗 Live Dashboard

[NovaTech Revenue Intelligence Dashboard](https://us-west-2.quicksight.aws.amazon.com/sn/account/UdacityQuicksightLab/accounts/548602084193/dashboards/d14515fc-5eaf-450b-959b-96d3f335a496)

---

## 📌 Project Overview

NovaTech's revenue data is distributed across **CRM, Marketing, and Customer Support** systems. This project brings these sources together in Amazon QuickSight to provide a consolidated view of sales performance, marketing effectiveness, and customer health.

The dashboard was developed using **Amazon QuickSight SPICE**, with source-specific datasets and a unified account-level dataset used for cross-domain analysis.

The project includes:

- Data preparation and validation
- SPICE dataset ingestion
- Data-type corrections
- Calculated fields
- A unified dataset joining CRM, Marketing, and Support data
- Three interactive dashboard sheets
- Filters and dashboard interactions
- Cross-sheet navigation
- Amazon QuickSight Q&A / Topic configuration
- Before-and-after Q&A validation
- Dashboard annotations
- Stakeholder-facing analysis and recommendations
- Published dashboard and PDF export
- Verification and exploration logs

---

## 📁 Repository Structure

```text
NovaTech-Revenue-Intelligence-Dashboard/
│
├── README.md
│
├── evidence_guide.md
├── exec_summary.md
├── methodology.md
├── q_exploration_log.md
├── stakeholder_report.md
├── verification_log.md
│
└── NovaTech_Project/
    │
    ├── documents/
    │   └── Supporting project documents
    │
    ├── pdfs/
    │   └── Dashboard PDF export
    │
    └── screenshots/
        ├── 1.jpeg – 23.jpeg
        └── 24.png – 47.png
```

The screenshots folder contains the visual evidence collected during data preparation, dashboard construction, Q&A configuration, publication, filtering, and navigation.

---

## 📊 Data Sources

| Dataset                            | Source Rows | Key Field    | Purpose                                  |
| ---------------------------------- | ----------: | ------------ | ---------------------------------------- |
| `novatech_crm_deals.csv`           |         499 | `account_id` | Sales pipeline and deal performance      |
| `novatech_marketing_campaigns.csv` |       2,240 | `account_id` | Campaign performance and marketing spend |
| `novatech_support_tickets.csv`     |       3,000 | `account_id` | Customer support and health analysis     |
| Unified dataset                    |        >499 | `account_id` | Cross-domain customer analysis           |

---

## 🔧 Data Preparation

Steps included:

* Imported all three source CSV files into **Amazon QuickSight SPICE**.
* Verified source row counts against expected datasets.
* Corrected date and numerical fields.
* Created business calculations (won deals, sales-cycle duration, marketing ROI).
* Built unified dataset using left joins on `account_id`.
* Checked for duplication and fan-out effects.
* Validated dashboard values independently.

### Data-quality observations

* Duplicate identifiers in some sources.
* Missing sentiment values.
* Support records without CRM accounts.
* Marketing records without CRM accounts.
* Row inflation due to one-to-many relationships.

---

## 📈 Dashboard Structure

Three sheets:

| Sheet                | Primary Dataset | Purpose                                                                  |
| -------------------- | --------------- | ------------------------------------------------------------------------ |
| **Marketing Funnel** | Marketing       | Campaign responses, spending, revenue, and marketing performance         |
| **Sales Pipeline**   | CRM             | Deal pipeline, win rate, revenue, regions, and losses                    |
| **Customer Health**  | Unified         | Customer support activity, account health, and priority-related analysis |

---

## 🔍 Key Findings

### Sales Performance
* **315 of 499 deals won** → **63.1% win rate**  
* Won revenue ≈ **$707,201**  
* Regional differences in win rates and revenue

### Marketing Performance
* Campaign spending ≈ **$12.36M**  
* Attributed revenue ≈ **$1.13M**  
* Overall marketing return strongly negative  
* All six programs show negative ROI  
* **Direct Mail** has strongest conversion response

### Customer Health
* **ACCT-041** logged **334 tickets** (highest volume)  
* Unified dataset connects support activity with revenue  
* Priority analysis shows resolution differences by ticket severity

---

## 🤖 QuickSight Q&A / Topic

Workflow:

1. Initial questions before Topic setup  
2. Topic creation and configuration  
3. Dataset scoping  
4. Instructions and setup  
5. Post-configuration Q&A  
6. Comparison with verified dashboard values  
7. Documentation of grain-related aggregate issues  

---

## 🎛️ Dashboard Interactivity

Includes:

* Sheet-level filters  
* Interactive filtering between visuals  
* Cross-sheet navigation  
* Published dashboard views  
* Evidence in screenshots  

---

## 📝 Dashboard Annotations

Annotations answer:

1. **What does the data show?**  
2. **Why does it matter?**  
3. **What action should the team take?**

---

## 📋 Supporting Documentation

- `verification_log.md` → Independent checks  
- `q_exploration_log.md` → Five exploratory Q&A questions  
- `methodology.md` → Data prep, validation, joins  
- `exec_summary.md` → Concise findings summary  
- `stakeholder_report.md` → Report for **Sarah Chen**  
- `evidence_guide.md` → Evidence mapping  

---

## 📂 Evidence

Located in `NovaTech_Project/screenshots/`:

* QuickSight setup  
* Dataset ingestion & validation  
* Calculated fields  
* Dataset joins  
* Dashboard construction  
* KPI visuals  
* Filters & interactions  
* Topic configuration  
* Q&A testing  
* Publication & navigation  
* Final dashboard state  

PDF export available in `pdfs/`.

---

## ✅ Project Checklist

* [x] CRM, Marketing, Support datasets prepared  
* [x] SPICE ingestion complete  
* [x] Data corrections applied  
* [x] Calculations created  
* [x] Unified dataset built  
* [x] Dashboard sheets created  
* [x] KPIs included  
* [x] Filters & interactions configured  
* [x] Cross-sheet navigation enabled  
* [x] Q&A Topic configured  
* [x] Evidence collected  
* [x] Logs documented  
* [x] Reports prepared  
* [x] Dashboard published & exported  

---

## 🛠️ Technology

* **Amazon QuickSight**  
* **QuickSight SPICE**  
* **QuickSight Q&A / Topics**  
* **CSV datasets**  
* Independent validation  

---

*Built as part of the Udacity Future AWS Agentic AI Business Professional program.*  
