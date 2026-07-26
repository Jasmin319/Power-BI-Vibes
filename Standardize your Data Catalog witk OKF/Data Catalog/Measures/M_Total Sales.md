# Measure: Total Sales

## Measure Group

- Sales
- _Measures table

---

## DAX

~~~dax
SUMX(Fact_OrderDetail, Fact_OrderDetail[Unit Price] * Fact_OrderDetail[Quantity Ordered] * (1 - Fact_OrderDetail[Discount Rate]))
~~~

---

## Technical Description

### Measure
**Name:** Total Sales  
**Purpose:** Total net sales for all order lines, calculated as Unit Price x Quantity Ordered x (1 - Discount Rate). Uses line item detail and reflects current filter context.

### Inputs & Dependencies
**No direct column references:** No

**Used measures:**
- None

**Used columns:** 
- 'Fact_OrderDetail'[Discount Rate]
- 'Fact_OrderDetail'[Quantity Ordered]
- 'Fact_OrderDetail'[Unit Price]

**Used tables:**
- [Fact_OrderDetail](../Tables/Facts/Fact_OrderDetail.md)

### DAX Functions
- SUMX

### Filter Behavior
- Inherits all report filters: Yes
- Additional filters/overrides:
  - None

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
**Name:** Total Sales

### Business Meaning
Total net sales for all order lines, calculated as Unit Price x Quantity Ordered x (1 - Discount Rate). Uses line item detail and reflects current filter context.

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
- None

---

## Change History

| Date | Author | Change | Impact |
|---|---|---|---|
| 2026-07-19 | AI Assistant | Initial documentation created from semantic model | Model documentation set |
| | | | |

---

## Source (Comment from Model)

Total net sales for all order lines, calculated as Unit Price x Quantity Ordered x (1 - Discount Rate). Uses line item detail and reflects current filter context.


