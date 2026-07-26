# Measure: Total Sales - YTD

## Measure Group

- Sales
- _Measures table

---

## DAX

~~~dax
CALCULATE([Total Sales], 'Time Intelligence'[Time Intelligence] = "YTD")
~~~

---

## Technical Description

### Measure
**Name:** Total Sales - YTD  
**Purpose:** Total Sales year-to-date based on Dim_Calendar[Date]. Applies Time Intelligence calculation item 'YTD'.

### Inputs & Dependencies
**No direct column references:** No

**Used measures:**
- [Total Sales](M_Total%20Sales.md)

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
**Data type:** Currency  
**FormatString:** $#,0.00  
**DisplayFolder:** Sales

### Special Considerations & Pitfalls
- Validate expected behavior under cross-filtering from all dimension tables.
- Time Intelligence variants depend on Dim_Calendar and calculation group configuration.
- Changes to base measures can impact derived period measures.

---

## Business Description

### KPI
**Name:** Total Sales - YTD

### Business Meaning
Total Sales year-to-date based on Dim_Calendar[Date]. Applies Time Intelligence calculation item 'YTD'.

### Calculation Basis
The KPI is based on:
- Semantic model tables and relationships
- DAX logic defined in the formula above
- Current filter context plus explicit measure filters

### Unit & Interpretation
**Unit:** Currency

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
- [Total Sales](./M_Total%20Sales.md)

---

## Change History

| Date | Author | Change | Impact |
|---|---|---|---|
| 2026-07-19 | AI Assistant | Initial documentation created from semantic model | Model documentation set |
| | | | |

---

## Source (Comment from Model)

Total Sales year-to-date based on Dim_Calendar[Date]. Applies Time Intelligence calculation item 'YTD'.




