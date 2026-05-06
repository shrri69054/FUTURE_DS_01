# 📊 Business Sales Performance Analytics

> **Future Interns — Data Science & Analytics | Task 1 (2026)**  
> A client-ready sales analytics dashboard built with Python and Tableau, analysing revenue trends, category performance, and regional profitability across 935 transactions (2022–2024).

---

## 🔍 Problem Statement

A retail business needed clarity on three key questions:

- Which products and categories generate the most revenue?
- How do sales and profits trend across months and years?
- Which regions are underperforming — and where should the business focus to grow faster?

---

## 📁 Project Structure

```
business-sales-analytics/
│
├── data/
│   ├── sales_data.csv          # 935 transaction-level records (2022–2024)
│   └── monthly_summary.csv     # Pre-aggregated monthly revenue & profit
│
├── dashboard/
│   └── sales_dashboard.twbx    # Tableau packaged workbook
│
├── notebooks/
│   └── analysis.ipynb          # Python EDA and chart generation (optional)
│
└── README.md
```

---

## 📊 Dashboard Preview

The interactive dashboard covers:

| Section | Charts |
|---|---|
| KPI Summary | Total Revenue · Profit · Margin · Orders · Avg Order Value |
| Revenue Trend | 36-month line chart (Revenue vs Profit) |
| Category Breakdown | Donut chart — Technology / Furniture / Office Supplies |
| Regional Performance | Bar chart — West / East / Central / South |
| Top 10 Products | Ranked horizontal bar table by revenue |

---

## 🗂️ Dataset

**Source:** Simulated superstore-style sales dataset (based on Kaggle Superstore structure)  
**Rows:** 935 orders | **Period:** Jan 2022 – Dec 2024 | **Format:** CSV

### Key columns

| Column | Description |
|---|---|
| `Order ID` | Unique order identifier |
| `Order Date` | Date of order (YYYY-MM-DD) |
| `Region` | West · East · Central · South |
| `Category` | Technology · Furniture · Office Supplies |
| `Product Name` | Individual product |
| `Sales` | Revenue per order line ($) |
| `Profit` | Net profit per order line ($) |
| `Profit Margin` | Profit as % of Sales |
| `Discount` | Discount applied (0–0.3) |
| `Segment` | Consumer · Corporate · Home Office |

---

## 💡 Key Business Insights

**1. Q4 seasonal spike**  
Revenue surges 28–34% every November–December. Recommendation: pre-stock Technology SKUs by October and launch targeted promotions in Q3.

**2. Technology leads; Furniture drags margins**  
Technology drives 37% of revenue at a 17.1% profit margin. Furniture generates similar revenue but only a 6.9% margin — supplier contracts or low-margin SKU discontinuation should be evaluated.

**3. West & East are core markets**  
These two regions contribute 61% of total revenue. Central and South are underpenetrated — targeted outreach or regional pricing could unlock 15–20% incremental growth.

**4. Central region margin decline**  
Revenue is growing but Central's profit margin dropped from 14.2% (2022) to 11.1% (2024). Root cause likely: aggressive discounting and rising logistics costs.

**5. Top 10 products drive 22% of revenue**  
Flagship SKUs (Canon Copier, Cisco TelePresence, Motorola Phones) deserve prioritised inventory management and bundling strategies to increase average order value.

---

## 🛠️ Tools Used

- **Python** — data generation, cleaning, and aggregation (`csv`, `datetime`, `random`)
- **Tableau** — interactive dashboard (revenue trend, category/region charts, KPI tiles)
- **Excel / CSV** — data storage and transfer format

---

## 🚀 How to Reproduce

### Option A — Tableau

1. Download `data/sales_data.csv`
2. Open Tableau → *Connect → Text File* → select the CSV
3. Recreate charts:
   - **Revenue Trend:** `Order Date` (Month) → Columns | `Sales` → Rows | Line chart
   - **Category Breakdown:** `Category` → Columns | `Sales` → Rows | Pie or Bar
   - **Regional Performance:** `Region` → Columns | `Sales` → Rows | Bar chart
   - **Top Products:** `Product Name` → Rows | `Sales` → Columns | Sort descending
4. Add KPI tiles using *Show Me → Text Table* with `SUM(Sales)`, `SUM(Profit)`, `AVG(Profit Margin)`

### Option B — Python (optional)

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('data/sales_data.csv', parse_dates=['Order Date'])

# Monthly revenue trend
monthly = df.groupby(df['Order Date'].dt.to_period('M'))['Sales'].sum()
monthly.plot(title='Monthly Revenue Trend', figsize=(12, 4))
plt.tight_layout()
plt.savefig('revenue_trend.png', dpi=150)

# Category breakdown
df.groupby('Category')['Sales'].sum().plot.pie(autopct='%1.1f%%')
plt.title('Revenue by Category')
plt.savefig('category_breakdown.png', dpi=150)
```

---

## 📈 Results Summary

| Metric | Value |
|---|---|
| Total Revenue (3 yr) | $2.30M |
| Total Profit (3 yr) | $286K |
| Overall Profit Margin | 12.4% |
| Total Orders | 935 |
| Average Order Value | $230 |
| Top Region | West (31.6%) |
| Top Category | Technology (37.2%) |
| Top Product | Canon imageCLASS Copier ($61,599) |

---

## 🏆 Skills Demonstrated

- Data cleaning & preparation
- Business KPI design and calculation
- Revenue trend and seasonality analysis
- Profit margin and category profitability analysis
- Regional performance benchmarking
- Business insight generation and recommendations
- Dashboard design for client-ready presentation

---

## 📬 Contact

Built as part of the **Future Interns Data Science & Analytics Programme — Task 1 (2026)**  
Feel free to connect on [LinkedIn](#) or raise an issue in this repository.

---

*Dataset is simulated for learning purposes, modelled on the structure of the [Kaggle Superstore Dataset](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final).*
