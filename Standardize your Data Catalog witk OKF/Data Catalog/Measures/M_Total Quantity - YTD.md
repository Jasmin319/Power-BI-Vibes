# Measure: Total Quantity - YTD

## Measure Group

- Orders
- _Measures table

---

## DAX

~~~dax
CALCULATE([Total Quantity], 'Time Intelligence'[Time Intelligence] = "YTD")
~~~

---

## Technical Description

### Measure
**Name:** Total Quantity - YTD  
**Purpose:** Total Quantity year-to-date based on Dim_Calendar[Date]. Applies Time Intelligence calculation item 'YTD'.

### Inputs & Dependencies
**No direct column references:** No

**Used measures:**
- [Total Quantity](M_Total%20Quantity.md)

**Used columns:** 
- 'Time Intelligence'[Time Intelligence]

**Used tables:**
- [Time Intelligence](../Tables/Time%20Intelligence.md)

### DAX Functions
- CALCULATE

### Filter Behavior
- Inherits all report filters: Yes
- Additional filters/overrides:
  - 'Time Intelligence'[Time Intelligence] = "YTD"

### Output & Format
**Data type:** Whole Number / Decimal  
**FormatString:** 0  
**DisplayFolder:** Orders

### Special Considerations & Pitfalls
- Validate expected behavior under cross-filtering from all dimension tables.
- Time Intelligence variants depend on Dim_Calendar and calculation group configuration.
- Changes to base measures can impact derived period measures.

---

## Business Description

### KPI
**Name:** Total Quantity - YTD

### Business Meaning
Total Quantity year-to-date based on Dim_Calendar[Date]. Applies Time Intelligence calculation item 'YTD'.

### Calculation Basis
The KPI is based on:
- Semantic model tables and relationships
- DAX logic defined in the formula above
- Current filter context plus explicit measure filters

### Unit & Interpretation
**Unit:** Count / Number

**Positive/Negative interpretation:**
- Higher value means: Better performance depends on KPI intent and report context.
- Lower value means: Opposite direction; interpret with business context.

### Filter Dependencies
The KPI responds to the following dimensions:
- Time period (date/month/quarter/year)
- Customer
- Employee
- Product/category
- Shipping context

### Exceptions & Limits
This KPI can be misinterpreted if model filters, relationship directions, or Time Intelligence settings are changed.

---

## References & Links

### Related Measures
- [Total Quantity](./M_Total%20Quantity.md)

---

## Change History

| Date | Author | Change | Impact |
|---|---|---|---|
| 2026-07-19 | AI Assistant | Initial documentation created from semantic model | Model documentation set |
| | | | |

---

## Source (Comment from Model)

Total Quantity year-to-date based on Dim_Calendar[Date]. Applies Time Intelligence calculation item 'YTD'.




