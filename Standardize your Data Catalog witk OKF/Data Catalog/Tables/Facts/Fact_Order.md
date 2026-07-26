## Table: Fact_Order

### Quick Overview
**Role:** Fact  
**Source:** orders.csv (Power Query import)  
**Description:** Order header fact table with customer, employee, shipper, key dates, and freight metrics.  
**Last updated:** 2026-07-19  
**Owner:** TBD  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | Fact table |
| **Description** | Stores one record per order with references to customer, employee, shipper, and delivery timeline fields. |
| **Query ID / Object ID** | lineageTag: b999d181-150c-408f-bd61-5ff421608dc4 |
| **Type** | Fact table |
| **Load-enabled** | Yes (import partition) |
| **Source system** | Local file source via Power Query |
| **Source object** | orders.csv |
| **Granularity** | One row represents one order |
| **Primary key** | Order ID |
| **Important foreign keys** | Customer ID, Employee ID, Shipper ID, Order Date |
| **Business purpose** | Core table for order lifecycle, shipping timeliness, and freight analysis. |
| **Usage for business users** | Analyze order counts, late deliveries, and shipping costs. |
| **Special logic** | Calculated columns Days to Ship and Days Late; source dates shifted +10 years in Power Query. |
| **Usage notes** | Several technical keys are hidden in model but used for relationships. |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| Order ID | Integer | Key | Unique order identifier. Source: orderID |
| Customer ID | Text | Foreign Key, Hidden | Customer reference. Source: customerID |
| Employee ID | Integer | Foreign Key, Hidden | Employee reference. Source: employeeID |
| Order Date | Date | Foreign Key, Hidden | Order placement date. Source: orderDate |
| Required Delivery Date | Date | Required | Promised delivery date. Source: requiredDate |
| Shipped Date | Date | Optional | Actual shipped date. Source: shippedDate |
| Shipper ID | Integer | Foreign Key, Hidden | Shipper reference. Source: shipperID |
| Freight Cost | Decimal | Measure Input | Freight charge amount. Source: freight |
| Days to Ship | Integer (calculated) | Derived | Date difference between required and shipped date. |
| Days Late | Integer (calculated) | Derived | Late indicator based on Days to Ship logic. |

---

## Key Overview

### Primary Key
- **Column name:** Order ID
- **Data type:** Integer
- **Property:** Not explicitly unique in metadata
- **Description:** Business order identifier used to join order details.

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| Customer ID | Text | Dim_Customer[Customer ID] | Connects order to customer dimension. |
| Employee ID | Integer | Dim_Employee[Employee ID] | Connects order to sales employee. |
| Shipper ID | Integer | Dim_Shipper[Shipper ID] | Connects order to shipping provider. |
| Order Date | Date | Dim_Calendar[Date] | Connects order to date dimension. |
| | | | |

---

## Relationships

### Incoming Relationships (foreign keys referencing this table)
- **[Fact_OrderDetail](Fact_OrderDetail.md)[Order ID]** -> **[Fact_Order](Fact_Order.md)[Order ID]**
  - Cardinality: 1:N
  - Filter direction: Single

### Outgoing Relationships (this table references others)
- **[Fact_Order](Fact_Order.md)[Customer ID]** -> **[Dim_Customer](../Dimensions/Dim_Customer.md)[Customer ID]**
  - Cardinality: N:1
  - Filter direction: Single
- **[Fact_Order](Fact_Order.md)[Employee ID]** -> **[Dim_Employee](../Dimensions/Dim_Employee.md)[Employee ID]**
  - Cardinality: N:1
  - Filter direction: Single
- **[Fact_Order](Fact_Order.md)[Shipper ID]** -> **[Dim_Shipper](../Dimensions/Dim_Shipper.md)[Shipper ID]**
  - Cardinality: N:1
  - Filter direction: Single
- **[Fact_Order](Fact_Order.md)[Order Date]** -> **[Dim_Calendar](../Dimensions/Dim_Calendar.md)[Date]**
  - Cardinality: N:1
  - Filter direction: Single

---

## Usage and Context

### Used Measures
- Order Count
- Late Orders Count
- Late Orders %
- Average Days to Ship

### Reporting Context
- Dashboards/reports that use this table:
  - Order pipeline and shipping performance reports.

---

## Maintenance Notes

- Source query adds 10 years to date fields; keep this transformation documented for data interpretation.
