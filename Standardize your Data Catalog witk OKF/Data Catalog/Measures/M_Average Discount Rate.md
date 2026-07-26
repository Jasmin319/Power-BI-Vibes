# Measure: Average Discount Rate

## Measure Group

- Discounts
- _Measures table

---

## DAX

~~~dax
AVERAGE(Fact_OrderDetail[Discount Rate])
~~~

---

## Technical Description

### Measure
**Name:** Average Discount Rate  
**Purpose:** Average line-item discount rate (0-1 scale) across the current filter context.

### Inputs & Dependencies
**No direct column references:** No

**Used measures:**
- None

**Used columns:** 
- 'Fact_OrderDetail'[Discount Rate]

**Used tables:**
- [Fact_OrderDetail](<../Tables/Facts/Fact_OrderDetail.md>)

### DAX Functions
- AVERAGE

### Filter Behavior
- Inherits all report filters: Yes
- Additional filters/overrides:
  - None

### Output & Format
**Data type:** Percentage  
**FormatString:** 0.00%  
**DisplayFolder:** Discounts

### Special Considerations & Pitfalls
- Validate expected behavior under cross-filtering from all dimension tables.
- Time Intelligence variants depend on Dim_Calendar and calculation group configuration.
- Changes to base measures can impact derived period measures.

---

## Business Description

### KPI
**Name:** Average Discount Rate

### Business Meaning
Average line-item discount rate (0-1 scale) across the current filter context.

### Calculation Basis
The KPI is based on:
- Semantic model tables and relationships
- DAX logic defined in the formula above
- Current filter context plus explicit measure filters

### Unit & Interpretation
**Unit:** %

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

Average line-item discount rate (0-1 scale) across the current filter context.


