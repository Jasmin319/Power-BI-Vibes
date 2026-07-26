## Table: Dim_Employee

### Quick Overview
**Role:** Dimension  
**Source:** employees.csv (Power Query import)  
**Description:** Employee master data with organizational and location attributes for sales and operations analysis.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Dimension table |
| **Description** | Employee lookup with name, role, geography, and reporting hierarchy fields. |
| **Query ID / Object ID** | lineageTag: 4812e149-57cb-454a-865c-4bede550e9a4 |
| **Type** | Dimension table |
| **Load-enabled** | Yes (import partition) |
| **Source system** | Local file source via Power Query |
| **Source object** | employees.csv |
| **Granularity** | One row represents one employee |
| **Primary key** | Employee ID (unique integer key) |
| **Important foreign keys** | Referenced by Fact_Order[Employee ID] |
| **Business purpose** | Supports performance analysis by sales representative and organizational structure. |
| **Usage for business users** | Filter KPIs by employee, job title, city, and country. |
| **Special logic** | Calculated column Last Name extracted from Employee Name. |
| **Usage notes** | Reports To Employee ID can be used for hierarchy modeling. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Employee ID | Integer | Key, Unique | Unique identifier for each employee. Source: employeeID |
| Employee Name | Text | Required | Full employee name. Source: employeeName |
| Job Title | Text | Optional | Employee role/title. Source: title |
| City | Text | Optional | Employee city. Data category: City. Source: city |
| Country | Text | Optional | Employee country. Data category: Country. Source: country |
| Reports To Employee ID | Integer | Optional | Manager/supervisor employee ID. Source: reportsTo |
| Last Name | Text (calculated) | Derived | Surname parsed from Employee Name. |

---

## Key Overview

### Primary Key
- **Column name:** Employee ID
- **Data type:** Integer
- **Property:** Unique
- **Description:** Unique employee key used in order ownership analysis.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| None | - | - | This dimension does not reference other tables. |
| | | | |

---

## Relationships

### Incoming Relationships (foreign keys referencing this table)
- **[Fact_Order](../Facts/Fact_Order.md)[Employee ID]** -> **[Dim_Employee](Dim_Employee.md)[Employee ID]**
  - Cardinality: 1:N
  - Filter direction: Single

### Outgoing Relationships (this table references others)
- None

---

## Usage and Context

### Used Measures
- No direct measure references found; used as a slicer/grouping dimension for order and sales metrics.

### Reporting Context
- Dashboards/reports that use this table:
  - Sales performance by employee and role.

---

## Maintenance Notes

- Loaded from employees.csv and typed in Power Query.
- Verify name parsing logic for edge cases in Last Name calculation.
