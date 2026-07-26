## Table: _Measures

### Quick Overview
**Role:** Metadata  
**Source:** Measure table (calculated DATATABLE partition)  
**Description:** Central container table for model measures, including base KPIs and time-intelligence variants.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Metadata table |
| **Description** | Dedicated measure table used to organize DAX measures by folders (Sales, Orders, Discounts, Shipping). |
| **Query ID / Object ID** | lineageTag: 79a0eadc-efaa-4cff-a9a8-875007cbb17a |
| **Type** | Metadata table |
| **Load-enabled** | Yes (calculated import partition) |
| **Source system** | Semantic model measure definitions |
| **Source object** | DAX measures + DATATABLE("Measure", INTEGER, {{1}}) |
| **Granularity** | Not transactional; one technical row plus measure definitions |
| **Primary key** | N/A |
| **Important foreign keys** | None |
| **Business purpose** | Central place to define and manage model-wide business KPIs. |
| **Usage for business users** | Consume standardized KPIs in visuals and reports. |
| **Special logic** | Contains base measures and many time-intelligence wrappers. |
| **Usage notes** | Hidden technical column Measure is only used to materialize table structure. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Measure | Integer | Hidden, Technical | Placeholder column from DATATABLE partition. |

---

## Key Overview

### Primary Key
- **Column name:** N/A
- **Data type:** N/A
- **Property:** N/A
- **Description:** Measure table does not use a business key.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| None | - | - | This table does not use relationships. |
| | | | |

---

## Relationships

### Incoming Relationships (foreign keys referencing this table)
- None

### Outgoing Relationships (this table references others)
- None

---

## Usage and Context

### Used Measures
- Base measures: Total Sales, Total Quantity, Order Count, Average Order Value, Total Discount Amount, Average Discount Rate, Late Orders Count, Late Orders %, Average Days to Ship.
- Time-intelligence measure variants: Current, Prior Year, YoY, YoY %, YTD, QTD, MTD for core KPIs.

### Reporting Context
- Dashboards/reports that use this table:
  - All reports consuming business KPIs from the semantic model.

---

## Maintenance Notes

- Keep this table as the single source of truth for KPI logic and naming conventions.
- Validate alignment with Measure Catalog documentation entries.
