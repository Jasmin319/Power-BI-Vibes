## Table: Time Intelligence

### Quick Overview
**Role:** Metadata  
**Source:** Calculation group table  
**Description:** Calculation group that applies common time transformations (Current, Prior Year, YoY, YTD, QTD, MTD) to selected measures.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Metadata table |
| **Description** | Calculation-group-backed table used to drive reusable time intelligence behavior across measures. |
| **Query ID / Object ID** | lineageTag: 81570185-5c04-4201-a1a3-2fdb4aedebc7 |
| **Type** | Metadata table |
| **Load-enabled** | Yes (calculation group partition) |
| **Source system** | Semantic model calculation group |
| **Source object** | calculationGroup with 7 calculation items |
| **Granularity** | One row represents one time intelligence calculation item |
| **Primary key** | Time Intelligence (calculation item name) |
| **Important foreign keys** | None |
| **Business purpose** | Standardizes period-over-period and to-date calculations for all selected measures. |
| **Usage for business users** | Switch metric view between current, prior year, YoY, and cumulative periods. |
| **Special logic** | Uses SELECTEDMEASURE and SAMEPERIODLASTYEAR/TOTALYTD/TOTALQTD/TOTALMTD. |
| **Usage notes** | Depends on Dim_Calendar[Date] for date intelligence calculations. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Time Intelligence | Text | Key (logical) | Name of calculation item applied to selected measure. |

---

## Key Overview

### Primary Key
- **Column name:** Time Intelligence
- **Data type:** Text
- **Property:** Logical key
- **Description:** Distinguishes calculation items in the calculation group.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| None | - | - | This table does not reference other tables through relationships. |
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
- Applied across base measures in _Measures using CALCULATE with Time Intelligence item filters.

### Reporting Context
- Dashboards/reports that use this table:
  - Any report that supports period switching (Current vs Prior Year, YTD/QTD/MTD).

---

## Maintenance Notes

- Maintain precedence and item naming consistency to avoid breaking existing report filters.
