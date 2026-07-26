## Table: Measure Catalog

### Quick Overview
**Role:** Metadata  
**Source:** Calculated table (DAX DATATABLE)  
**Description:** Internal catalog table documenting measure names, expressions, format strings, and descriptions.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Metadata table |
| **Description** | Documentation support table containing textual metadata about model measures. |
| **Query ID / Object ID** | lineageTag: 9e1091d4-ff9f-4842-9b4b-5dfe3367f15b |
| **Type** | Metadata table |
| **Load-enabled** | Yes (calculated import partition) |
| **Source system** | Semantic model calculated table |
| **Source object** | DAX DATATABLE expression |
| **Granularity** | One row represents one documented measure variant |
| **Primary key** | Measure Name (logical key) |
| **Important foreign keys** | None |
| **Business purpose** | Centralized in-model reference for measure documentation and governance. |
| **Usage for business users** | Review measure definitions and intended semantics. |
| **Special logic** | Static DATATABLE with predefined documentation records. |
| **Usage notes** | Useful for measure dictionary visuals and QA checks. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Measure Name | Text | Key (logical) | Name of the documented measure. |
| DAX Expression | Text | Required | DAX definition string. |
| Format String | Text | Optional | Display format string for the measure. |
| Description | Text | Optional | Business/technical description of the measure. |

---

## Key Overview

### Primary Key
- **Column name:** Measure Name
- **Data type:** Text
- **Property:** Logical key
- **Description:** Identifier for measure documentation entries.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| None | - | - | This metadata table does not reference other tables. |
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
- Not a measure computation source; stores documentation content only.

### Reporting Context
- Dashboards/reports that use this table:
  - Measure dictionary or documentation pages.

---

## Maintenance Notes

- Keep entries synchronized with actual measures in _Measures and calculation groups.
