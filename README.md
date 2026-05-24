# Supply Chain Management: OTIF Performance Analytics Dashboard

A multi-page Power BI dashboard built on a star-schema data model to track supply chain delivery performance across customers, products, and cities. The dashboard measures On-Time (OT%), In-Full (IF%), and On-Time In-Full (OTIF%) metrics against targets — the three core KPIs of supply chain service levels.

**Author:** Ashwin Suryawanshi | **Tool:** Power BI Desktop

---

## Files in This Repository

| File | Description |
|------|-------------|
| `Supply_Chain_Management.pbix` | Power BI dashboard — 3 pages, KPI visuals, pivot tables with sparklines, charts |

---

## Tools & Technologies

- **Power BI Desktop** — KPI visuals, pivot tables, sparklines, donut chart, column chart, line chart, slicers
- **Data Model:** Star schema — 4 tables (`fact_order_lines`, `fact_orders_aggregate`, `dim_customers`, `dim_products`, `dim_targets_orders`, `dim_date`)

---

## Data Model (Star Schema)

| Table | Type | Key Fields |
|-------|------|------------|
| `fact_order_lines` | Fact | `order_qty`, `delivery_qty`, `Not_Delivered`, `LIFR%`, `VOFR%`, `Week_Num`, `Month`, `Year` |
| `fact_orders_aggregate` | Fact | `IF%`, `OT%`, `OTIF%` |
| `dim_customers` | Dimension | `customer_name`, `city` |
| `dim_products` | Dimension | `product_name`, `category` |
| `dim_targets_orders` | Dimension | `IF_Avg`, `OT_Avg`, `OTIF_Avg` (target benchmarks) |
| `dim_date` | Dimension | `date` (with Month hierarchy) |

---

## KPI Definitions

| KPI | Full Name | Description |
|-----|-----------|-------------|
| `OT%` | On-Time % | % of orders delivered on or before promised date |
| `IF%` | In-Full % | % of orders delivered with complete quantity |
| `OTIF%` | On-Time In-Full % | % of orders that were both on-time AND in-full |
| `LIFR%` | Line Fill Rate % | % of order lines fulfilled completely |
| `VOFR%` | Volume Fill Rate % | % of total ordered volume actually delivered |

---

## Dashboard Pages (3)

### Page 1 — Executive Overview
| Visual | Type | Fields | Purpose |
|--------|------|--------|---------|
| IF% vs Target | KPI Visual | IF%, IF_Avg target, Year trend | In-Full rate vs benchmark |
| OT% vs Target | KPI Visual | OT%, OT_Avg target, Year trend | On-Time rate vs benchmark |
| OTIF% vs Target | KPI Visual | OTIF%, OTIF_Avg target, Year trend | Combined OTIF vs benchmark |
| LIFR% | Card | LIFR% | Line fill rate headline |
| VOFR% | Card | VOFR% | Volume fill rate headline |
| Total Order Qty | Card | Sum of order_qty | Total units ordered |
| Total Delivery Qty | Card | Sum of delivery_qty | Total units delivered |
| Customer KPI Table | Pivot Table | customer_name, IF%, OT%, OTIF%, LIFR%, VOFR% | All KPIs per customer in one view |
| City KPI Table | Pivot Table | city, IF%/target, OT%/target, OTIF%/target | City-level performance vs targets |
| Month Slicer | Slicer | Date → Month | Filter all visuals by month |

### Page 2 — Product Analysis
| Visual | Type | Fields | Purpose |
|--------|------|--------|---------|
| Product LIFR% & VOFR% | Pivot Table + Sparklines | product_name, LIFR%, VOFR%, weekly sparklines | Per-product fill rates with trend sparklines |
| Order vs Delivery by Category | Clustered Column Chart | category, order_qty, delivery_qty | Order fulfillment gap by product category |
| Undelivered Orders by City | Donut Chart | city, Not_Delivered | City-wise undelivered order share |

### Page 3 — Customer & Order Deep Dive
| Visual | Type | Fields | Purpose |
|--------|------|--------|---------|
| Orders by Customer | Column Chart | customer_name, order_qty | Volume per customer |
| Orders by Product | Clustered Bar | product_name, order_qty | Top ordered products |
| Monthly Order Trend | Line Chart | Month, order_qty | Order volume trend over time |
| Total Order Qty | Card | Sum of order_qty | Page-level order total |
| Total Delivery Qty | Card | Sum of delivery_qty | Page-level delivery total |
| Not Delivered | Card | Sum of Not_Delivered | Undelivered units count |
| City Slicer | Slicer | city | Filter all visuals by city |

---

## Key Insights Enabled

- **OTIF gap analysis** — KPI visuals with targets immediately show if service levels are below benchmark
- **Customer scorecards** — pivot table on Page 1 ranks all customers by every KPI in one view
- **Product fill rate trends** — sparklines on Page 2 reveal week-over-week LIFR/VOFR trends per product
- **Category fulfillment gap** — column chart shows which product categories have the largest order vs delivery shortfall
- **City-level undelivered share** — donut chart highlights which cities account for most failed deliveries
- **Monthly demand trends** — line chart on Page 3 tracks order volume changes over time

---

## Suggested Repo Name

`Supply-Chain-OTIF-Analytics-PowerBI`

---

## Topics

`power-bi` `supply-chain` `otif` `data-analysis` `kpi-dashboard` `business-intelligence` `logistics` `data-visualization`
