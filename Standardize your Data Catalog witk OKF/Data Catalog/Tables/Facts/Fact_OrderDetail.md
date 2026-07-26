## Table: Fact_OrderDetail

### Quick Overview
**Role:** Fact  
**Source:** order_details.csv (Power Query import)  
**Description:** Order line-item fact table containing product-level quantities, prices, discounts, and line revenue calculations.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Fact table |
| **Description** | Stores one row per order line with product, quantity, unit price, discount, and derived revenue/discount amounts. |
| **Query ID / Object ID** | lineageTag: 391c6cb7-e7a6-4777-9937-37e37f572251 |
| **Type** | Fact table |
| **Load-enabled** | Yes (import partition) |
| **Source system** | Local file source via Power Query |
| **Source object** | order_details.csv |
| **Granularity** | One row represents one product line in one order |
| **Primary key** | Composite key candidate: Order ID + Product ID |
| **Important foreign keys** | Order ID -> Fact_Order, Product ID -> Dim_Product |
| **Business purpose** | Provides transactional detail for sales, quantity, and discount analytics. |
| **Usage for business users** | Analyze product sales performance and discount impact at line level. |
| **Special logic** | Calculated columns Line Revenue and Discount Amount. |
| **Usage notes** | Primary source for sales amount and quantity-based KPIs. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Order ID | Integer | Foreign Key, Hidden | Parent order reference. Source: orderID |
| Product ID | Integer | Foreign Key, Hidden | Ordered product reference. Source: productID |
| Unit Price | Decimal | Measure Input | Line item unit price. Source: unitPrice |
| Quantity Ordered | Integer | Measure Input | Quantity sold in the line item. Source: quantity |
| Discount Rate | Decimal | Measure Input | Discount percentage in 0-1 scale. Source: discount |
| Line Revenue | Decimal (calculated) | Derived | Net line revenue after discount. |
| Discount Amount | Decimal (calculated) | Derived | Monetary discount amount per line. |

---

## Key Overview

### Primary Key
- **Column name:** Order ID + Product ID
- **Data type:** Integer + Integer
- **Property:** Composite candidate (not explicitly marked unique)
- **Description:** Typical line-level grain key identifying product within an order.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| Order ID | Integer | Fact_Order[Order ID] | Links line item to order header. |
| Product ID | Integer | Dim_Product[Product ID] | Links line item to product attributes. |
| | | | |

---

## Relationships

### Incoming Relationships (foreign keys referencing this table)
- None

### Outgoing Relationships (this table references others)
- **[Fact_OrderDetail](Fact_OrderDetail.md)[Order ID]** -> **[Fact_Order](Fact_Order.md)[Order ID]**
  - Cardinality: N:1
  - Filter direction: Single
- **[Fact_OrderDetail](Fact_OrderDetail.md)[Product ID]** -> **[Dim_Product](../Dimensions/Dim_Product.md)[Product ID]**
  - Cardinality: N:1
  - Filter direction: Single

---

## Usage and Context

### Used Measures
- Total Sales
- Total Quantity
- Total Discount Amount
- Average Discount Rate

### Reporting Context
- Dashboards/reports that use this table:
  - Product-level sales and discount analysis reports.

---

## Maintenance Notes

- Loaded from order_details.csv with typed numeric and percentage fields.
- Ensure discount column remains in decimal fraction format (0-1).
