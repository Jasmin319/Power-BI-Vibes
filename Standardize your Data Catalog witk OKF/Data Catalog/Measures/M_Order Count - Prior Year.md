# Measure: Order Count - Prior Year

## Measure Group

- Orders
- _Measures table

---

## DAX

~~~dax
CALCULATE([Order Count], 'Time Intelligence'[Time Intelligence] = "Prior Year")
~~~

---

## Technical Description

### Measure
**Name:** Order Count - Prior Year  
**Purpose:** Order Count for the same period in the prior year. Applies Time Intelligence calculation item 'Prior Year'.

### Inputs & Dependencies
**No direct column references:** No

**Used measures:**
- [Order Count](M_Order%20Count.md)

**Used columns:** 
- 'Time Intelligence'[Time Intelligence]

**Used tables:**
- [Time Intelligence](../Tables/Time%20Intelligence.md)

### DAX Functions
- CALCULATE

### Filter Behavior
- Inherits all report filters: Yes
- Additional filters/overrides:
  - 'Time Intelligence'[Time Intelligence] = "Prior Year"

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
**Name:** Order Count - Prior Year

### Business Meaning
Order Count for the same period in the prior year. Applies Time Intelligence calculation item 'Prior Year'.

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
- [Order Count](./M_Order%20Count.md)

---

## Change History

| Date | Author | Change | Impact |
|---|---|---|---|
| 2026-07-19 | AI Assistant | Initial documentation created from semantic model | Model documentation set |
| | | | |

---

## Source (Comment from Model)

Order Count for the same period in the prior year. Applies Time Intelligence calculation item 'Prior Year'.




