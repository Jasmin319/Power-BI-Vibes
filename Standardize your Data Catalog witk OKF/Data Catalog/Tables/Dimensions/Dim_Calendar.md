## Table: Dim_Calendar

### Quick Overview
**Role:** Dimension  
**Source:** Calculated table (DAX calendar from Fact_Order dates)  
**Description:** Date dimension spanning order activity with year/month/quarter/week/day attributes for time intelligence analysis.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Dimension table |
| **Description** | Calendar table generated from order, required delivery, and shipped dates to support trend and period analysis. |
| **Query ID / Object ID** | lineageTag: 25046128-70c4-4f69-935a-dddc51c58913 |
| **Type** | Dimension table |
| **Load-enabled** | Yes (calculated import partition) |
| **Source system** | Semantic model calculated table |
| **Source object** | DAX CALENDAR/GENERATE expression |
| **Granularity** | One row represents one calendar date |
| **Primary key** | Date (unique date key) |
| **Important foreign keys** | Referenced by Fact_Order[Order Date] |
| **Business purpose** | Provides a conformed date axis for all time-based analysis and time intelligence. |
| **Usage for business users** | Slice KPIs by date, month, quarter, week, and day of week. |
| **Special logic** | Uses UNION of three Fact_Order date columns and generates derived date attributes. |
| **Usage notes** | Core dependency for calculation group Time Intelligence. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Date | Date | Key, Unique | Calendar date used as primary date key. |
| Year | Integer | Required | Four-digit calendar year. |
| Month Number | Integer | Required | Month number from 1 to 12. |
| Month Name | Text | Required | Full month name for display. |
| Quarter | Text | Required | Quarter label (Q1-Q4). |
| Week Number | Integer | Required | Week number of year. |
| Month Start Date | Date | Optional | First day of the month for the date row. |
| Month End Date | Date | Optional | Last day of the month for the date row. |
| Day of Week | Text | Optional | Day name (for example Monday). |

---

## Key Overview

### Primary Key
- **Column name:** Date
- **Data type:** Date
- **Property:** Unique
- **Description:** Unique date key used for joining fact table date columns.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| None | - | - | This dimension does not reference other tables. |
| | | | |

---

## Relationships

### Incoming Relationships (foreign keys referencing this table)
- **[Fact_Order](../Facts/Fact_Order.md)[Order Date]** -> **[Dim_Calendar](Dim_Calendar.md)[Date]**
  - Cardinality: 1:N
  - Filter direction: Single

### Outgoing Relationships (this table references others)
- None

---

## Usage and Context

### Used Measures
- Used indirectly by all time-intelligence versions of core measures via the Time Intelligence calculation group.

### Reporting Context
- Dashboards/reports that use this table:
  - Any trend report by date, month, quarter, or YTD/QTD/MTD.

---

## Maintenance Notes

- Date range is driven by min/max of Fact_Order date columns.
- Keep this table marked as the model date table if required by report logic.
