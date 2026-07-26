## Table: Dim_Product

### Quick Overview
**Role:** Dimension  
**Source:** products.csv (Power Query import)  
**Description:** Product master table with pricing, package, status, and category attributes for product-level analytics.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Dimension table |
| **Description** | Product catalog containing identifiers, names, prices, package quantities, and category assignment. |
| **Query ID / Object ID** | lineageTag: 513130d5-04ec-4f37-af44-1cb2a7d0f732 |
| **Type** | Dimension table |
| **Load-enabled** | Yes (import partition) |
| **Source system** | Local file source via Power Query |
| **Source object** | products.csv |
| **Granularity** | One row represents one product |
| **Primary key** | Product ID (unique integer key) |
| **Important foreign keys** | Category ID -> Dim_Category[Category ID] |
| **Business purpose** | Enables product mix, pricing, and category performance analysis. |
| **Usage for business users** | Filter and compare KPIs by product attributes and lifecycle status. |
| **Special logic** | Calculated column Cancelled = IF(Is Discontinued=1,"X",""). |
| **Usage notes** | Category ID is hidden but required for model relationship. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Product ID | Integer | Key, Unique | Unique identifier for each product. Source: productID |
| Product Name | Text | Required | Product business name. Source: productName |
| Package Quantity | Text | Optional | Quantity/unit per package. Source: quantityPerUnit |
| Unit Price | Decimal | Required | Standard product unit price. Source: unitPrice |
| Is Discontinued | Integer | Required | Product active status flag (1 = discontinued). Source: discontinued |
| Category ID | Integer | Foreign Key, Hidden | Product category reference. Source: categoryID |
| Cancelled | Text (calculated) | Derived | Text flag for discontinued products. |

---

## Key Overview

### Primary Key
- **Column name:** Product ID
- **Data type:** Integer
- **Property:** Unique
- **Description:** Unique product key used by order line details.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| Category ID | Integer | Dim_Category[Category ID] | Assigns each product to one category. |
| | | | |

---

## Relationships

### Incoming Relationships (foreign keys referencing this table)
- **[Fact_OrderDetail](../Facts/Fact_OrderDetail.md)[Product ID]** -> **[Dim_Product](Dim_Product.md)[Product ID]**
  - Cardinality: 1:N
  - Filter direction: Single

### Outgoing Relationships (this table references others)
- **[Dim_Product](Dim_Product.md)[Category ID]** -> **[Dim_Category](Dim_Category.md)[Category ID]**
  - Cardinality: N:1
  - Filter direction: Single

---

## Usage and Context

### Used Measures
- Product filters affect sales, quantity, discount, and shipping measures through Fact_OrderDetail.

### Reporting Context
- Dashboards/reports that use this table:
  - Product and category performance reports.

---

## Maintenance Notes

- Loaded from products.csv with typed fields in Power Query.
- Review whether Cancelled should be Boolean instead of text marker.
