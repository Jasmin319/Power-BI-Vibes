## Table: Dim_Shipper

### Quick Overview
**Role:** Dimension  
**Source:** shippers.csv (Power Query import)  
**Description:** Shipping carrier lookup used to analyze fulfillment and logistics performance by shipper.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Dimension table |
| **Description** | Shipper reference table with shipping company identifiers and names. |
| **Query ID / Object ID** | lineageTag: 0e8e4ffb-281b-4b5e-8135-5e145e4fa288 |
| **Type** | Dimension table |
| **Load-enabled** | Yes (import partition) |
| **Source system** | Local file source via Power Query |
| **Source object** | shippers.csv |
| **Granularity** | One row represents one shipping company |
| **Primary key** | Shipper ID (unique integer key) |
| **Important foreign keys** | Referenced by Fact_Order[Shipper ID] |
| **Business purpose** | Enables carrier-level delivery and freight analysis. |
| **Usage for business users** | Compare logistics KPIs by shipper. |
| **Special logic** | None beyond standard import and typing. |
| **Usage notes** | Small lookup table used as a slicer and grouping dimension. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Shipper ID | Integer | Key, Unique | Unique identifier for each shipping company. Source: shipperID |
| Company Name | Text | Required | Shipping company name. Source: companyName |

---

## Key Overview

### Primary Key
- **Column name:** Shipper ID
- **Data type:** Integer
- **Property:** Unique
- **Description:** Unique shipper key used by order records.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| None | - | - | This dimension does not reference other tables. |
| | | | |

---

## Relationships

### Incoming Relationships (foreign keys referencing this table)
- **[Fact_Order](../Facts/Fact_Order.md)[Shipper ID]** -> **[Dim_Shipper](Dim_Shipper.md)[Shipper ID]**
  - Cardinality: 1:N
  - Filter direction: Single

### Outgoing Relationships (this table references others)
- None

---

## Usage and Context

### Used Measures
- No direct measure references found; used to segment freight and shipping KPIs.

### Reporting Context
- Dashboards/reports that use this table:
  - Shipping and fulfillment performance reports.

---

## Maintenance Notes

- Loaded from shippers.csv with straightforward schema.
