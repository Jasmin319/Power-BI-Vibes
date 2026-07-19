# Measure Documentation Template

This template documents a single DAX measure completely and in a structured way.

---

# Measure: [Measure Name]

## Measure Group

- [Associated Measure Group](G_[Category]__[Group%20Name].md)
- [Additional related measures]

---

## DAX

```dax
[Insert DAX formula here]
```

---

## Technical Description

### Measure
**Name:** [Measure Name]  
**Purpose:** [Short description - What does this measure calculate?]

### Inputs & Dependencies
**No direct column references:** [Yes/No]

**Used measures:**
- [Measure 1]
- [Measure 2]

**Used columns:** 
- 'TableName'[ColumnName]

**Used tables:**
- [TableName]

### DAX Functions
- [CALCULATE]
- [SUM]
- [FILTER]
- [More...]

### Filter Behavior
- Inherits all report filters: [Yes/No]
- Additional filters/overrides:
  - [e.g. 'Time Intelligence'[Time Intelligence] = "YoY"]

### Output & Format
**Data type:** [Whole Number / Decimal / Text / etc.]  
**FormatString:** [e.g. #,##0 or 0.00%; -0.00%; 0.00%]  
**DisplayFolder:** [e.g. Shipping / Financials / No assignment]

### Special Considerations & Pitfalls
- [Special consideration 1 - What should be kept in mind?]
- [Special consideration 2 - Performance considerations?]
- [Special consideration 3 - Known limitations?]

---

## Business Description

### KPI
**Name:** [Business name]

### Business Meaning
[Describe why this KPI is important and how it supports business decision-making]

### Calculation Basis
The KPI is based on:
- [Data sources]
- [Logic/transformations]
- [Filters from DAX or report context]

### Unit & Interpretation
**Unit:** [e.g. count, EUR, days, %, etc.]

**Positive/Negative interpretation:**
- Higher value means: [Interpretation]
- Lower value means: [Interpretation]

### Filter Dependencies
The KPI responds to the following dimensions:
- Time period (date/month/quarter/year)
- [Geographic dimension]
- [Organizational dimension]
- [Product/business dimension]
- [More...]

### Exceptions & Limits
[Describe when this KPI is NOT meaningful or could be misinterpreted]

---

## References & Links

### Related Measures
- [Related Measure 1]
- [Related Measure 2]


---

## Change History

| Date | Author | Change | Impact |
|---|---|---|---|
| [Date] | [Name] | [What was changed] | [Which reports are affected] |
| | | | |

---

## Source (Comment from Model)

[Optional comment from Power BI model metadata]

