## Table: Dim_Customer

### Quick Overview
**Role:** Dimension  
**Source:** customers.csv (Power Query import)  
**Description:** Master data for all customers including company name, contact information, and geographic location. Enables analysis of sales by customer and region.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Dimension table |
| **Description** | Customer master table with business identity, contact, and location attributes used to slice order data. |
| **Query ID / Object ID** | lineageTag: 951a36d3-d10e-4eeb-8958-21b14381c7a7 |
| **Type** | Dimension table |
| **Load-enabled** | Yes (import partition) |
| **Source system** | Local file source via Power Query |
| **Source object** | customers.csv |
| **Granularity** | One row represents one customer company |
| **Primary key** | Customer ID (unique text key) |
| **Important foreign keys** | Referenced by Fact_Order[Customer ID] |
| **Business purpose** | Provides customer context for order and sales analysis. |
| **Usage for business users** | Filter and compare metrics by customer, company, city, and country. |
| **Special logic** | Calculated column Country Code = UPPER(LEFT([Country],3)). |
| **Usage notes** | Country is tagged with geographic data categories (City, Country). Country Code logic currently returns 3 letters. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Customer ID | Text | Key, Unique | Unique identifier for each customer company. Source: customerID |
| Company Name | Text | Required | Official registered name of the customer company. Source: companyName |
| Contact Name | Text | Optional | Primary business contact person. Source: contactName |
| Contact Title | Text | Optional | Job title of the primary contact. Source: contactTitle |
| City | Text | Optional | City of the customer business location. Data category: City. Source: city |
| Country | Text | Optional | Country of the customer. Data category: Country. Source: country |
| Country Code | Text (calculated) | Derived | Uppercase 3-character code derived from Country. |

---

## Key Overview

### Primary Key
- **Column name:** Customer ID
- **Data type:** Text
- **Property:** Unique
- **Description:** Business key used to uniquely identify each customer and join to order facts.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| None | - | - | This dimension does not reference other tables. |
| | | | |

---

## Relationships

### Incoming Relationships (foreign keys referencing this table)
- **[Fact_Order](../Facts/Fact_Order.md)[Customer ID]** -> **[Dim_Customer](Dim_Customer.md)[Customer ID]**
  - Cardinality: 1:N (Dim_Customer to Fact_Order)
  - Filter direction: Single

### Outgoing Relationships (this table references others)
- None

---

## Usage and Context

### Used Measures
- No direct measure references to Dim_Customer were found in measure tables.

### Reporting Context
- Dashboards/reports that use this table:
  - Any report visual filtered by customer attributes (Company Name, City, Country).

---

## Maintenance Notes

- Source query reads customers.csv and promotes headers in Power Query.
- Consider validating whether Country Code should be 2-letter (ISO alpha-2) or 3-letter output as currently implemented.
