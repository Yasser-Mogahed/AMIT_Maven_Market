<div align="center">

<img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" />
<img src="https://img.shields.io/badge/DAX-00B388?style=for-the-badge&logo=microsoft&logoColor=white" />
<img src="https://img.shields.io/badge/Data%20Modeling-2D6A4F?style=for-the-badge&logo=databricks&logoColor=white" />
<img src="https://img.shields.io/badge/Business%20Intelligence-1B4332?style=for-the-badge&logo=tableau&logoColor=white" />

<br/><br/>

```
███╗   ███╗ █████╗ ██╗   ██╗███████╗███╗   ██╗
████╗ ████║██╔══██╗██║   ██║██╔════╝████╗  ██║
██╔████╔██║███████║██║   ██║█████╗  ██╔██╗ ██║
██║╚██╔╝██║██╔══██║╚██╗ ██╔╝██╔══╝  ██║╚██╗██║
██║ ╚═╝ ██║██║  ██║ ╚████╔╝ ███████╗██║ ╚████║
╚═╝     ╚═╝╚═╝  ╚═╝  ╚═══╝  ╚══════╝╚═╝  ╚═══╝

███╗   ███╗ █████╗ ██████╗ ██╗  ██╗███████╗████████╗
████╗ ████║██╔══██╗██╔══██╗██║ ██╔╝██╔════╝╚══██╔══╝
██╔████╔██║███████║██████╔╝█████╔╝ █████╗     ██║   
██║╚██╔╝██║██╔══██║██╔══██╗██╔═██╗ ██╔══╝     ██║   
██║ ╚═╝ ██║██║  ██║██║  ██║██║  ██╗███████╗   ██║   
╚═╝     ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝   ╚═╝   
```

# 🌿 Maven Market — Business Intelligence Dashboard

**A full-scale Power BI solution transforming raw retail data into strategic intelligence.**  
*Built with dimensional modeling, DAX engineering, and executive-grade visual storytelling.*

---

[![Stars](https://img.shields.io/github/stars/Yasser-Mogahed/maven-market?color=52b788&style=flat-square)](https://github.com/Yasser-Mogahed/maven-market)
[![Last Commit](https://img.shields.io/github/last-commit/Yasser-Mogahed/maven-market?color=2d6a4f&style=flat-square)](https://github.com/Yasser-Mogahed/maven-market)
[![License](https://img.shields.io/badge/license-MIT-1b4332?style=flat-square)](LICENSE)

</div>

---

## 📌 Table of Contents

- [🧭 Project Overview](#-project-overview)
- [⚡ Live KPIs at a Glance](#-live-kpis-at-a-glance)
- [🗂️ Data Architecture](#️-data-architecture)
- [📊 Dashboard Pages](#-dashboard-pages)
- [🔢 DAX Measures & KPIs](#-dax-measures--kpis)
- [🖼️ Screenshots](#️-screenshots)
- [📁 Repository Structure](#-repository-structure)
- [🚀 How to Use](#-how-to-use)
- [💡 Key Insights](#-key-insights)
- [🛠️ Tech Stack](#️-tech-stack)
- [👤 Author](#-author)

---

## 🧭 Project Overview

> *"Data is the new oil — but only when refined."*

**Maven Market** is a multi-branch grocery retail company operating across the **USA, Canada, and Mexico**. This Power BI project serves as a centralized Business Intelligence solution that unifies sales, product, customer, and returns data into a single interactive reporting ecosystem.

### 🎯 Business Problem

Retail managers lacked visibility into:
- Which regions and stores drive the most profitability
- How customer segments behave differently across membership tiers
- Which products carry the highest margins — and which drag them down
- How returns impact overall revenue and operational efficiency

### ✅ Solution Delivered

A **4-page interactive Power BI report** with slicers, cross-filtering, KPI cards, map visuals, sankey-style decomposition, and time-intelligence analysis — all backed by a clean star schema data model.

---

## ⚡ Live KPIs at a Glance

<div align="center">

| 💰 Total Revenue | 🏆 Total Profit | 📈 Profit Margin | 🔄 Return Rate | 👥 Customers | 📦 Transactions |
|:---:|:---:|:---:|:---:|:---:|:---:|
| **$1.76M** | **$1.05M** | **60%** | **1%** | **10K** | **270K** |

</div>

---

## 🗂️ Data Architecture

The model follows a classic **Star Schema** — optimized for performance, clarity, and scalability.

```
                        ┌─────────────┐
                        │   Calendar  │ ◄── Time Intelligence
                        └──────┬──────┘
                               │
          ┌────────────────────▼──────────────────────┐
          │           Transactions_1997-1998           │  ◄── Primary Fact Table
          │  customer_id | product_id | store_id       │
          │  quantity | stock_date | transaction_date  │
          └──┬──────────────┬──────────────────────────┘
             │              │
    ┌────────▼───┐    ┌─────▼──────┐    ┌──────────────┐
    │  Customers │    │  Products  │    │    Stores    │
    └────────────┘    └────────────┘    └──────┬───────┘
                                               │
                                        ┌──────▼───────┐
                                        │   Regions    │ ◄── sales_district, sales_region
                                        └──────────────┘

          ┌─────────────────────────────────────────────┐
          │           Returns_1997-1998                 │  ◄── Secondary Fact Table
          │  product_id | store_id | quantity | date    │
          └─────────────────────────────────────────────┘
```

### Tables Summary

| Table | Type | Key Fields |
|---|---|---|
| `Transactions_1997-1998` | 📊 Fact | customer_id, product_id, store_id, quantity, date |
| `Returns_1997-1998` | 📊 Fact | product_id, store_id, quantity, return_date |
| `Products` | 📋 Dimension | product_id, brand, cost, retail_price, weight |
| `Customers` | 📋 Dimension | customer_id, city, country, member_card, education |
| `Stores` | 📋 Dimension | store_id, region_id, city, country, store_type |
| `Regions` | 📋 Dimension | region_id, sales_district, sales_region |
| `Calendar` | 📅 Date Table | date, day, month, quarter, year |

> All relationships are **One-to-Many** from dimension → fact tables, following BI best practices.

---

## 📊 Dashboard Pages

### 🏠 1. Executive Overview
*The command center — high-level performance at a glance.*

- **Profit Margin & Revenue by Country** — Azure map bubble chart
- **Monthly Profit & Revenue** — dual-line trend chart (1997–1998)
- **Total Profit by Store Country** — bar comparison (USA dominates at ~700K)
- **Total Profit by Sales Region** — North West leads at ~500K
- **Filters:** Month slider · Store Country · Year (1997/1998)

---

### 🛍️ 2. Products
*Where costs meet margins — product intelligence.*

- **Brand-level matrix** — cost, retail price, weight, low_fat %, profit margin, recyclable count
- **Total Profit vs Total Revenue** — donut (62.63% profit share)
- **Profit Margin by Brand** — ADJ tops at **68.84%**, Quick at **68.48%**
- **Filters:** Product Brand · Store City · Store Country

---

### 👥 3. Customers
*Who buys, how much, and why it matters.*

- **Decomposition flow** — Profit → State → Sales Region → Member Card → Gender
- **Profit by Membership** — Bronze dominates at **55.91%**
- **Revenue by Education** — Partial High School leads at **$533.19K**
- **Filters:** Member Card · Store Country · Education level

---

### 🔄 4. Returns
*The quality pulse — low returns, high satisfaction.*

- **Total Revenue by Region** — world map view
- **Total Returns by Store Type** — Supermarkets lead (3,204 returns)
- **Monthly Return Rate** — trend from 13% → ~10% (downward = improving)
- **Return Rate by Brand** — King highest at **1.8%**, Genteel at **1.5%**
- **Filters:** Product Brand · Store Type · Month slider

---

## 🔢 DAX Measures & KPIs

```dax
-- Total Revenue
Total Revenue = SUMX(Transactions_1997-1998, 
    Transactions_1997-1998[quantity] * RELATED(Products[product_retail_price]))

-- Total Cost
Total Cost = SUMX(Transactions_1997-1998, 
    Transactions_1997-1998[quantity] * RELATED(Products[product_cost]))

-- Total Profit
Total Profit = [Total Revenue] - [Total Cost]

-- Profit Margin %
Profit Margin % = DIVIDE([Total Profit], [Total Revenue])

-- Return Rate %
Return Rate % = DIVIDE([Total Quantity Returned], [Total Quantity Sold])

-- Total Customers
Total Customers = DISTINCTCOUNT(Transactions_1997-1998[customer_id])

-- Transactions Count
Transactions Count = COUNTROWS(Transactions_1997-1998)
```

---

## 🖼️ Screenshots

<div align="center">

### 🏠 Executive Overview
![Executive Overview](Executive_Overview.png)

### 🛍️ Products Page
![Products](Products.png)

### 👥 Customers Page
![Customers](Customers.png)

### 🔄 Returns Page
![Returns](Returns.png)

### 🗺️ Data Model Schema
![Schema](Schema.png)

</div>

---

## 📁 Repository Structure

```
maven-market/
│
├── 📊 Maven_Market_Graduation_Project.pbix   # Main Power BI Report File
├── 📄 Maven_Market_Report.pdf                # Project Documentation (9 pages)
│
├── 🖼️ Screenshots/
│   ├── Executive_Overview.png
│   ├── Products.png
│   ├── Customers.png
│   ├── Returns.png
│   └── Schema.png
│
└── 📋 README.md
```

---

## 🚀 How to Use

### Prerequisites
- **Power BI Desktop** (free) — [Download here](https://powerbi.microsoft.com/desktop/)

### Steps

```bash
# 1. Clone this repository
git clone https://github.com/Yasser-Mogahed/maven-market.git

# 2. Open the report
# Navigate to the folder and double-click:
Maven_Market_Graduation_Project.pbix

# 3. Explore
# Use the left navigation panel to switch between report pages.
# Apply slicers to filter by country, year, brand, education, and more.
```

> **Note:** No external database connection required. All data is embedded in the `.pbix` file.

---

## 💡 Key Insights

| # | Insight | Impact |
|---|---|---|
| 🥇 | **USA generates ~67%** of total profit | Core market — prioritize US store performance |
| 🥈 | **Bronze members account for 55.91%** of membership profit | Loyalty program expansion opportunity |
| 🥉 | **ADJ brand leads with 68.84% margin** | Consider increasing ADJ product shelf space |
| 🔴 | **Partial High School customers** drive the most revenue ($533K) | Surprising segment — targeted marketing potential |
| ✅ | **1% return rate** across 270K transactions | Excellent product-market fit and quality control |
| 📉 | Monthly return rate **declining from 13% → 10%** | Positive trend — quality improvements working |
| 🌍 | **North West region** is the top-performing sales region | Potential for replicating success in underperforming regions |

---

## 🛠️ Tech Stack

<div align="center">

| Tool | Purpose |
|---|---|
| ![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat-square&logo=powerbi&logoColor=black) | Report development & visualization |
| ![DAX](https://img.shields.io/badge/DAX-00B388?style=flat-square&logo=microsoft&logoColor=white) | KPI calculations & measures |
| ![Power Query](https://img.shields.io/badge/Power%20Query-2D6A4F?style=flat-square&logo=microsoft&logoColor=white) | Data transformation & ETL |
| ![Star Schema](https://img.shields.io/badge/Star%20Schema-1B4332?style=flat-square&logo=databricks&logoColor=white) | Dimensional data modeling |
| ![Azure Maps](https://img.shields.io/badge/Azure%20Maps-0078D4?style=flat-square&logo=microsoftazure&logoColor=white) | Geographic visualizations |

</div>

---

## 👤 Author

<div align="center">

**Yasser Ahmed Mogahed**

*Data Analyst | Business Intelligence Developer*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/yasser-mogahed)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github)](https://github.com/Yasser-Mogahed)

**Supervised by:** Ali Zein Elabdeen Mohamed Abdelnaby · Yasser Ahmed Mogahed

---

*If this project helped or inspired you, please consider giving it a ⭐ — it means a lot!*

</div>

---

<div align="center">

```
Made with 💚 and Power BI
Maven Market Intelligence Dashboard © 2024
```

</div>
