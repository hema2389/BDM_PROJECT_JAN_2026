# BDM Capstone Project — IIT Madras Online BS Degree Program
## Demand Forecasting & Menu Optimization for a Cloud Kitchen

**Student:** M. Hema Varshni (24f1001256)  
**Grade:** B 
**Organisation:** Padma's Home Food
**Data Period:** April 1 – May 26, 2025 (49 operational days)

---

## Project Overview

This project analyses 567 real orders from a home cloud kitchen in Chennai to solve three recurring operational problems using data-driven methods. All data is **primary** — collected directly from the business owner through structured interviews and Cookr app order history.

---

## Problem Statements

| # | Problem | Impact |
|---|---|---|
| PS1 | Unpredictable demand → emergency procurement on Zepto/Swiggy at 20–140% markup | Margin erosion |
| PS2 | Thursday lunch surges → cook exhaustion → unplanned kitchen closures | ₹9,718 revenue loss per closure |
| PS3 | No dish-level profitability visibility → loss-making dishes undetected | Ven Pongal sold at –1.8% CM |

---

## Datasets

| Dataset | Rows | Description |
|---|---|---|
| `Order_Data.csv` | 567 | Order ID, Date, Day, Category, Type, Dish Name, Quantity, Value |
| `Menu_Details.csv` | 114 | Dish names, prep time, selling prices, ingredients |
| `Ingredient_Costs.csv` | 86 | Local vendor vs Quick Commerce prices for 87 ingredients |
| `Operational_Events.csv` | 14 | Festivals, holidays, closure events |

---

## Methods Used

### 1. Demand Forecasting (PS1)
- **7-Day Moving Average** — smoothed baseline capturing weekly cycle
- **Exponential Smoothing** (α = 0.3) — adaptive forecast, tested α = 0.1 to 0.4
- **MAPE = 25.51%** (excluding kitchen closure days)

### 2. Inventory Optimisation (PS1)
- **ABC Classification** — 16 ingredients ranked by annual value; 7 Class A items = 69.3% of spend
- **EOQ Formula** — `√(2DS/H)` — Toor Dal: 31.84 kg/order vs current 5–10 kg
- **ROP + Safety Stock** — `Z × σ × √(Lead Time)` at 95% service level (Z = 1.645)

### 3. Menu Profitability Analysis (PS3)
- **Contribution Margin** — `Selling Price − Ingredient Cost − Platform Fee (30%)`
- **Menu Engineering Matrix** — 20 dishes classified as Stars, Plowhorses, Puzzles, Dogs

### 4. Procurement Cost-Benefit Analysis (PS1)
- Markup % = `(QC Price − Local Price) / Local Price × 100`
- Tomato: +140% | Eggs: +133% | Chicken: +80%

---

## Key Findings

| Finding | Value |
|---|---|
| Daily order volatility (CV) | 44.44% |
| Thursday share of weekly orders | 17.64% (100 orders) |
| Lunch share of all orders | 74.1% |
| Regular order AOV | ₹302 |
| Subscription order AOV | ₹123 |
| Regular orders revenue share | 68.8% from 47.4% of volume |
| **Ven Pongal CM** | **–1.8% (sold at a LOSS)** |
| Best CM dish | White Rice — 49.4% |
| Tomato Quick Commerce markup | 140% |

---

## Recommendations & Impact

| PS | Recommendation | Projected Saving |
|---|---|---|
| PS1 | Sunday ES forecast review → Mon/Tue bulk procurement + ROP reference card | ₹18,000–30,000/year |
| PS2 | Daily order caps (Thu/Fri: 15, Mon–Wed: 18) + cross-train helper | ₹40,000/year recovered |
| PS3 | Remove Ven Pongal + Reprice Biryani ₹190→₹210 + promote Puzzles | +₹27,744/year contribution |
| **Total** | | **₹85,744–₹97,744/year** |

---

## Repository Structure

```
bdm-capstone-padmas-home-food/
│
├── data/
│   ├── Order_Data.csv
│   ├── Menu_Details.csv
│   ├── Ingredient_Costs.csv
│   └── Operational_Events.csv
│
├── notebooks/
│   └── BDM_PROJECT.ipynb          # Google Colab analysis notebook
│
├── excel/
│   └── MASTER_MENU_SPREADSHEET.xlsx   # All Excel sheets: Forecasting, ABC, EOQ, CM
│
├── report/
│   └── BDM_Final_Report_HemaVarshni_v2.docx
│
├── presentation/
│   └── BDM_Viva_FINAL.pptx
│
└── README.md
```

---

## Tools & Libraries

| Tool | Purpose |
|---|---|
| Microsoft Excel | Demand Forecasting, ABC, EOQ, ROP, Contribution Margin calculations |
| Python (Google Colab) | Data analysis, visualisation, ES forecast validation |
| pandas | Data loading, groupby, aggregation |
| matplotlib | Charts — daily trend, day-of-week bar, meal category pie, ES forecast |

---

## How to Run the Colab Notebook

1. Open `notebooks/BDM_PROJECT.ipynb` in Google Colab
2. Upload `data/Order_Data.csv` when prompted
3. Run all cells in order
4. Outputs: `daily_orders_trend.png`, `es_forecast.png`, `order_type.png`, `meal_category.png`, `forecasting_output.xlsx`

---

## Results — Charts

| Chart | Description |
|---|---|
| Daily Order Volume Trend | 3-phase demand pattern across 49 days |
| Orders by Day of Week | Thursday peak at 100 orders |
| Meal Category Split | Lunch = 74.1% |
| Actual vs ES Forecast | α=0.3, MAPE=25.51% |
| Orders & Revenue by Type | Regular 68.8% of revenue despite 47.4% of volume |
| ABC Classification | 7 Class A ingredients = 69.3% of annual spend |
| Menu Engineering Matrix | 5 Stars, 4 Plowhorses, 5 Puzzles, 3 Dogs (incl. 1 loss-maker) |

---

## About the Organisation

**Padma's Home Food** is a cloud kitchen operated by Mrs. Padmavathy Ravichandran through the [Cookr App](https://www.cookr.in) in Medavakkam, Chennai. Established February 2023. B2C model — 30+ authentic home-style Tamil dishes, served across breakfast, lunch, and dinner via regular and subscription orders.

*Data collected with written consent from the business owner. All customer personal information removed before analysis.*

---

## References

1. Krajewski, L. J. et al. — *Operations Management: Processes and Supply Chain* (12th Ed.)
2. Wirtz, J. & Lovelock, C. — *Services Marketing: People, Technology, Strategy*
3. Newbold, P. — *Statistics for Business and Economics*
4. Malhotra, N. & Dash, S. — *Marketing Research: An Applied Approach*
5. Kasavana, M. L. & Smith, D. I. (1982) — Menu Engineering: A Practical Guide

---

*BDM Capstone Project | IITM Online BS Degree Program | 2025*
