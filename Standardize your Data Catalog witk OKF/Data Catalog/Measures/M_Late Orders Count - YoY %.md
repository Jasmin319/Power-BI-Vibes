# Measure: Late Orders Count - YoY %

## Measure Group

- Shipping
- _Measures table

---

## DAX

~~~dax
CALCULATE([Late Orders Count], 'Time Intelligence'[Time Intelligence] = "YoY %")
~~~

---

## Technical Description

### Measure
**Name:** Late Orders Count - YoY %  
**Purpose:** Year-over-year percent change in Late Orders Count. Applies Time Intelligence calculation item 'YoY %'.

### Inputs & Dependencies
**No direct column references:** No

**Used measures:**
- [Late Orders Count](M_Late%20Orders%20Count.md)

**Used columns:** 
- 'Time Intelligence'[Time Intelligence]

**Used tables:**
- [Time Intelligence](../Tables/Time%20Intelligence.md)

### DAX Functions
- CALCULATE

### Filter Behavior
- Inherits all report filters: Yes
- Additional filters/overrides:
  - 'Time Intelligence'[Time Intelligence] = "YoY %"

### Output & Format
**Data type:** Percentage  
**FormatString:** 0.00%  
**DisplayFolder:** Shipping

### Special Considerations & Pitfalls
- Validate expected behavior under cross-filtering from all dimension tables.
- Time Intelligence variants depend on Dim_Calendar and calculation group configuration.
- Changes to base measures can impact derived period measures.

---

## Business Description

### KPI
**Name:** Late Orders Count - YoY %

### Business Meaning
Year-over-year percent change in Late Orders Count. Applies Time Intelligence calculation item 'YoY %'.

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
- [Late Orders Count](./M_Late%20Orders%20Count.md)

---

## Change History

| Date | Author | Change | Impact |
|---|---|---|---|
| 2026-07-19 | AI Assistant | Initial documentation created from semantic model | Model documentation set |
| | | | |

---

## Source (Comment from Model)

Year-over-year percent change in Late Orders Count. Applies Time Intelligence calculation item 'YoY %'.




