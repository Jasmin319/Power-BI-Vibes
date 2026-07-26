## Table: Dim_Category

### Quick Overview
**Role:** Dimension  
**Source:** categories.csv (Power Query import)  
**Description:** Product category master data used to classify products and support category-level analysis.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Dimension table |
| **Description** | Category lookup with category name and description for product hierarchy and grouping. |
| **Query ID / Object ID** | lineageTag: 35c2f614-0f4a-4c2a-bce3-0c3425bf4fb2 |
| **Type** | Dimension table |
| **Load-enabled** | Yes (import partition) |
| **Source system** | Local file source via Power Query |
| **Source object** | categories.csv |
| **Granularity** | One row represents one product category |
| **Primary key** | Category ID (unique integer key) |
| **Important foreign keys** | Referenced by Dim_Product[Category ID] |
| **Business purpose** | Enables category and sub-assortment performance analysis. |
| **Usage for business users** | Filter product-related KPIs by category. |
| **Special logic** | None beyond standard import and typing. |
| **Usage notes** | Table annotation shows PBI_ResultType = Exception; validate if intentional. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Category ID | Integer | Key, Unique | Unique identifier for each product category. Source: categoryID |
| Category Name | Text | Required | Business name of the category. Source: categoryName |
| Category Description | Text | Optional | Category description text. Source: description |

---

## Key Overview

### Primary Key
- **Column name:** Category ID
- **Data type:** Integer
- **Property:** Unique
- **Description:** Unique category key used for product classification.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| None | - | - | This dimension does not reference other tables. |
| | | | |

---

## Relationships

### Incoming Relationships (foreign keys referencing this table)
- **[Dim_Product](Dim_Product.md)[Category ID]** -> **[Dim_Category](Dim_Category.md)[Category ID]**
  - Cardinality: 1:N
  - Filter direction: Single

### Outgoing Relationships (this table references others)
- None

---

## Usage and Context

### Used Measures
- No direct measure references found; used through product-based filtering.

### Reporting Context
- Dashboards/reports that use this table:
  - Product and sales reports grouped by category.

---

## Maintenance Notes

- Loaded from categories.csv with typed columns in Power Query.
