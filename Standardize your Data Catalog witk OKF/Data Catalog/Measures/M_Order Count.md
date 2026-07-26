# Measure: Order Count

## Measure Group

- Orders
- _Measures table

---

## DAX

~~~dax
DISTINCTCOUNT(Fact_Order[Order ID])
~~~

---

## Technical Description

### Measure
**Name:** Order Count  
**Purpose:** Number of distinct orders based on Order ID in the current filter context.

### Inputs & Dependencies
**No direct column references:** No

**Used measures:**
- None

**Used columns:** 
- 'Fact_Order'[Order ID]

**Used tables:**
- [Fact_Order](../Tables/Facts/Fact_Order.md)

### DAX Functions
- DISTINCTCOUNT

### Filter Behavior
- Inherits all report filters: Yes
- Additional filters/overrides:
  - None

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
**Name:** Order Count

### Business Meaning
Number of distinct orders based on Order ID in the current filter context.

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
- None

---

## Change History

| Date | Author | Change | Impact |
|---|---|---|---|
| 2026-07-19 | AI Assistant | Initial documentation created from semantic model | Model documentation set |
| | | | |

---

## Source (Comment from Model)

Number of distinct orders based on Order ID in the current filter context.


