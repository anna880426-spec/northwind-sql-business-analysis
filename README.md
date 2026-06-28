# Northwind SQL Business Analysis

Analysing a real-world company dataset using SQL to support business decision-making across 5 departments — Product, Logistics, HR, Pricing, and Sales.

---

## Project Overview

This project uses **PostgreSQL** to query and analyse the Northwind dataset, a relational database modelling a food trading company's operations. The goal is to translate raw data into actionable business insights for multiple internal teams.

**Tools:** PostgreSQL · DBeaver  
**Skills:** Multi-table JOIN · Window Functions · CTEs · Aggregation · CASE WHEN · Subqueries · Date Calculations

---

## Dataset

The Northwind database contains 8 core tables representing a real-world business operation:

| Table | Description |
|-------|-------------|
| `products` | Product catalogue with pricing and stock levels |
| `categories` | Product category classification |
| `suppliers` | Supplier information by region |
| `orders` | Customer orders with shipping details |
| `order_details` | Line items per order with quantity and discount |
| `customers` | Customer profiles and locations |
| `employees` | Employee records and reporting structure |
| `shippers` | Shipping carrier information |

**Entity Relationship Diagram (ERD):**

![ERD](erd.png)

---

## Business Questions & Key Findings

### 🛒 Product Team
**Q1 — Active Products in Target Price Range ($20–$50)**  
Identified 27 active products within the pricing range, sorted by unit price. This supports the team's annual pricing strategy review.

---

### 🚚 Logistics Team
**Q2 — Countries with Poor Shipping Performance (1998)**  
Found 9 countries with average shipping delays of 5+ days and more than 10 orders. Sweden had the worst performance at an average of 13.29 days delay — a priority target for supplier contract review.

**Q4 — Monthly Order Volume & Freight (1997–1998)**  
April 1998 recorded the highest freight ($6,394) and order volume (74 orders). January–March 1998 also performed strongly, suggesting the company should concentrate marketing efforts in Q1–Q2.

**Q7 — Regional Supplier Stock Status by Category**  
Mapped inventory levels (stock, on-order, reorder) across America, Europe, and Asia-Pacific for all 8 product categories. Identified Meat/Poultry in Europe as a critical restocking concern (0 units across all metrics).

---

### 👥 HR Team
**Q3 — Employee Structure & Reporting Lines**  
Generated a full organisational report with employee age at hire, job title, and manager details. Found that 5 of 9 employees report directly to the VP of Sales, suggesting a flat structure that may benefit from additional management layers.

---

### 💰 Pricing Team
**Q5 — Products with Unusual Price Increases**  
Identified 2 products with price increases outside the 20–30% target range: Queso Cabrales (+50%) and Singaporean Hokkien Fried Mee (+43%), flagging them for pricing strategy review.

**Q6 — Sales Performance by Category & Price Range**  
Analysed total sales amount and order volume across 8 categories and 3 price bands. Dairy Products in the $20–$50 range generated the highest volume (204 orders, $146,783).

**Q8 — Product Positioning vs Category Average & Median Price**  
Compared each active product's unit price against its category average and median. Found that 43 out of 67 products are priced below category average — particularly in Beverages where 8 of 9 products fall below average.

---

### 📊 Sales Team
**Q9 — Employee Sales KPI Dashboard**  
Built a comprehensive KPI table per employee including total sales (with/without discount), unique order count, average order value, and discount percentage. Margaret Peacock led with $232,890 in total sales; Robert King had the highest discount rate at 11.84%.

**Q10 — Employee Sales Performance by Category**  
Calculated each employee's sales contribution per category, both as a share of their own total and as a share of company-wide revenue. Enables targeted performance reviews by product category.

---

## Repository Structure

```
northwind-sql-business-analysis/
├── README.md
├── erd.png                  # Entity Relationship Diagram
├── sql/
│   ├── question1.sql        # Product Team - active products
│   ├── question2.sql        # Logistics - shipping performance
│   ├── question3.sql        # HR - employee structure
│   ├── question4.sql        # Logistics - monthly performance
│   ├── question5.sql        # Pricing - price increase analysis
│   ├── question6.sql        # Pricing - sales by price range
│   ├── question7.sql        # Logistics - supplier stock status
│   ├── question8.sql        # Pricing - product price positioning
│   ├── question9.sql        # Sales - employee KPI
│   └── question10.sql       # Sales - performance by category
├── output/
│   ├── question1.csv
│   ├── question2.csv
│   └── ... (10 files)
└── report/
    └── analysis_report.pdf  # Full written analysis
```

---

## SQL Techniques Used

| Technique | Questions |
|-----------|-----------|
| Multi-table JOIN | Q1, Q2, Q3, Q6, Q7, Q9, Q10 |
| Window Functions (`OVER`, `PARTITION BY`) | Q5, Q8, Q10 |
| CTE (`WITH`) | Q8 |
| Subquery | Q10 |
| Date Calculations | Q2, Q3, Q4 |
| `CASE WHEN` | Q6, Q7, Q8 |
| `HAVING` | Q2, Q4, Q5 |
| `percentile_disc` (Median) | Q8 |
