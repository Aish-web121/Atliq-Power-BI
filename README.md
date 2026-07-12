# AtliQ Hardware — P&L & Business Performance Dashboard

> An 8-page enterprise Power BI dashboard covering financial performance (P&L), sales, market share, and supply chain analytics for AtliQ Hardware — built as a BI360-style capstone project.

---

## 📌 Overview

AtliQ Hardware operates across multiple markets and customer segments. This dashboard gives finance, sales, and executive teams a unified view of business performance — from gross sales down to net profit — with benchmark comparisons, year-over-year tracking, and forecast accuracy monitoring.

**Built with:** Power BI Desktop · DAX · Star Schema · Excel data sources

**Download the .pbix:** [v1.0 Release](https://github.com/Aish-web121/Atliq-Power-BI/releases/tag/v1.0)

---

## 📊 Dashboard Pages

| Page | Description |
|------|-------------|
| **Landing Page** | Navigation hub with branding and page links |
| **P&L Check** | Raw validation matrix — gross sales, net invoice sales, deductions, net sales by fiscal year |
| **Finance View** | Dynamic P&L matrix with trend charts, KPIs, and benchmark comparison |
| **Sales View** | Customer and product performance with scatter charts and donut breakdowns |
| **Market View** | Regional market analysis with waterfall chart and market share tracking |
| **Supply Chain View** | Forecast accuracy, net error, and absolute error by product/customer |
| **Sales Trend** | Standalone drill-down line chart for trend analysis |
| **Executive View** | Consolidated C-suite summary — ribbon chart, KPIs, top/bottom rankings |

---

## 🗂️ Data Model — Star Schema

### Fact Table
| Table | Key Columns |
|-------|-------------|
| `fact_actuals_estimates` | `gross_sales_amount`, `net_invoice_sales_amount`, `post_invoice_deductions_amount`, `post_invoice_other_deductions_amount`, `net_sales_amount` |

### Dimension Tables
| Table | Key Columns |
|-------|-------------|
| `dim_date` | `date`, `fiscal_year`, `quarters`, `ytd_ytg` |
| `dim_customer` | `customer`, `channel`, `market` |
| `dim_market` | `market`, `region` |
| `dim_product` | `product`, `category`, `segment`, `division` |

### Disconnected / Helper Tables
These have no direct relationships to the fact table — they drive dynamic report logic via DAX:

| Table | Purpose |
|-------|---------|
| `P & L` | Line Item & Description — drives the dynamic P&L matrix rows |
| `P & L column` | Column header labels for the P&L matrix |
| `Report_Measure` | Dedicated measure-holder table (20 measures) |
| `Set BM` | Benchmark parameter table |
| `Target Gap Tolerance` | What-if parameter table |
| `fiscal_year` | Slicer-friendly fiscal year parameter |
| `marketshare` | Manufacturer-level market share data |
| `Sub_zone` | Sub-zone mapping |

---

## 🧮 Key DAX Measures

All measures live in the `Report_Measure` table to keep the model clean.

### P&L Measures
| Measure | Description |
|---------|-------------|
| `P & L values final` | Core dynamic measure — uses `SWITCH(TRUE())` to render Gross Sales / Net Invoice Sales / Deductions / Net Sales based on selected Line Item |
| `Selected P & L value Row` | `SELECTEDVALUE`-based measure driving card visuals |
| `P & L BM` | Benchmark comparison value |
| `P & L LY` | Last year value |
| `P & L YoY` | Year-over-year absolute change |
| `P & L YoY %` | Year-over-year % change |

### Profitability Measures
| Measure | Description |
|---------|-------------|
| `GM %` | Gross Margin % |
| `GM % BM` | Gross Margin % vs benchmark |
| `Gross Margin $` | Gross Margin in absolute dollars |
| `Net Profit $` | Net Profit in absolute dollars |
| `Net Profit %` | Net Profit % |
| `NP % BM` | Net Profit % vs benchmark |

### Forecast & Error Measures
| Measure | Description |
|---------|-------------|
| `Forecast Accuracy %` | Forecast vs actual accuracy rate |
| `Forecast Accuracy % LY` | Last year forecast accuracy |
| `Absolute Error` | Mean absolute error |
| `Absolute Error LY` | Last year absolute error |
| `Net Error` | Net forecast error |
| `Net Error %` | Net error as a percentage |
| `Net error LY` | Last year net error |

### Other Measures
| Measure | Description |
|---------|-------------|
| `NS $` | Net Sales in dollars |
| `NS % BM` | Net Sales % vs benchmark |
| `AtliQ MS %` | AtliQ market share % |
| `Market Share %` | Overall market share |
| `Risk` | Risk-flagging text measure |
| `BM Message` | Benchmark status message |
| `Top / Bottom Product & Customers` | Ranking measure for top/bottom analysis |

---

## 🔽 Filters & Slicers

A consistent slicer panel is replicated across all major views:

- **Fiscal Year** — select the reporting year
- **YTD / YTG** — year-to-date or year-to-go toggle
- **Quarter** — Q1 / Q2 / Q3 / Q4
- **Region** — geographic filter
- **Market** — country/market filter
- **Customer** — specific customer
- **Segment** — product segment
- **Category** — product category
- **Product** — individual product
- **Benchmark Set** — switch between benchmark scenarios

Cross-page filter consistency ensures the same selections apply seamlessly across Finance, Sales, Market, Supply Chain, and Executive views.

---

## 🚀 How to Use

1. **Download** the `.pbix` file from the [v1.0 Release](https://github.com/Aish-web121/Atliq-Power-BI/releases/tag/v1.0)
2. **Open** in Power BI Desktop (free — [download here](https://powerbi.microsoft.com/desktop/))
3. Start on the **Landing Page** and use the navigation buttons to jump to any view
4. Use the **slicer panel** on the right to filter by fiscal year, market, customer, segment, etc.
5. On the **Finance View**, select a Line Item from the P&L matrix to see the dynamic measure switch in action
6. On the **Market View**, use the action buttons to drill into sub-regions
7. On the **Supply Chain View**, track forecast accuracy and error trends by product or customer

---

## 🛠️ Tech Stack

- **Power BI Desktop** — report building and data modeling
- **DAX** — all calculated measures and dynamic logic
- **Star Schema** — fact + dimension table design
- **Excel** — source data files
- **What-If Parameters** — for target gap tolerance and benchmark switching

---

## 📁 Project Structure

```
Atliq-Power-BI/
│
├── chapter-7-bi360.pbix     # Main Power BI report file (~244MB)
└── README.md
```

---

## 👤 Author

**Aishwarya Ranjan Srivastava**
[LinkedIn](https://www.linkedin.com/in/aishwarya-ranjan-srivastava) · [GitHub](https://github.com/Aish-web121)
