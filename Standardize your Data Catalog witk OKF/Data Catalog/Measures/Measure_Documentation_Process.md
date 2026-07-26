# Measure Documentation Process & Catalog Logic

## Overview

This document describes the logic and process for systematically documenting DAX measures in Power BI. It is based on the cowork skill approach from video 047 and extends it for structured measure cataloging.

---

## Process Overview

### Input
- TMDL code or a Power BI Desktop model with DAX measures
- Metadata: DisplayFolder, FormatString, table assignment
- Optional descriptions/comments from the model

### Tasks

#### 1. Extraction & Analysis
For EACH measure:
- Extract name, DAX formula, DisplayFolder, and FormatString
- Identify referenced measures
- Analyze referenced tables and columns
- Document DAX functions

Rule: Do not invent data. Document only elements that actually exist.

#### 2. Categorization
Assign all measures to 5 main categories:

| Category | Examples |
|---|---|
| **Time Intelligence** | YoY, QoQ, MTD, YTD, Prior Year, Growth % |
| **Aggregations** | SUM, COUNT, AVERAGE, MIN, MAX |
| **Calculated Ratios** | Margin %, Growth Rate, Turnover, Efficiency |
| **Financial** | Revenue, Cost, Profit, Variance, Budget vs Actual |
| **Custom/Domain-Specific** | Business-specific KPIs |

#### 3. Description & Documentation
**If a description is MISSING:**
- Write short, neutral, and functional text
- Example: "Calculates average days between order and shipment"
- DO NOT invent business details

**If a description EXISTS:**
- Use the existing description or refine it slightly

#### 4. Excel Catalog Structure
Create a structured Excel table with:

| Column | Description | Rule Set |
|---|---|---|
| **Name** | Measure name | Unique, exactly as in the model |
| **Description** | Short, functional description | Neutral, not invented |
| **DAX Formula** | Complete DAX formula | Word-for-word from model |
| **FormatString** | Format (e.g. #,##0; 0.00%) | Or empty if not defined |
| **Main Category** | One of the 5 categories | Mandatory field |
| **DisplayFolder** | Folder in the model | "No folder assigned" if empty |
| **Referenced Measures** | Comma-separated list | Or "References another measure" |
| **Referenced Columns** | 'TableName'[ColumnName] | Only explicitly referenced columns |
| **Referenced Tables** | Comma-separated list | "References another measure" if no direct reference |
| **Business Owner** | [Empty] | Fill manually |
| **Tech Owner** | [Empty] | Fill manually |
| **Status** | [Empty] | Fill manually (Active/Deprecated/To Review) |

#### 5. Sorting
- **Primary:** Main Category (alphabetical)
- **Secondary:** Measure Name (alphabetical)

#### 6. Individual Measure Documentation
For each important/critical measure:
- Use [Data Catalog/Measures/_template_measure_documentation.md](Data Catalog/Measures/_template_measure_documentation.md)
- Create a file: `M_[MeasureName].md`
- Fill in technical and business descriptions completely

---

## Workflow for Bulk Documentation (Cowork Skill Approach)

### Step 1: Input Template (TMDL Format)

```
Input: TMDL code with measures
Format: Name, DAX, DisplayFolder, FormatString, optional Description
```

### Step 2: Processing Logic

**Guardrails (Never fabricate, Always verify):**
- No invented descriptions
- Only document what exists in code/model
- Do not add business details if unclear
- Use functional, neutral descriptions
- No invalid references
- Only explicitly mentioned tables/columns

### Step 3: Output Format

**Excel table with:**
- Alphabetical sorting
- 5 categories
- All 12 columns from the catalog structure

**Individual markdown files for critical measures:**
- Filename: `M_[CategoryShort]_[MeasureName].md`
- Template: [Data Catalog/Measures/_template_measure_documentation.md](Data Catalog/Measures/_template_measure_documentation.md)

### Step 4: Quality Control

Verify:
- [ ] All measures captured?
- [ ] No invented descriptions?
- [ ] Correct categorization?
- [ ] DAX formulas complete and correct?
- [ ] References accurate?
- [ ] Sorting correct?

---

## Best Practices

### Descriptions
- **GOOD:** "Calculates revenue minus cost of goods sold"
- **BAD:** "Profit - this is critical for management"
- **BAD:** "Revenue metric (invented, not in model)"

### Categorization
- **GOOD:** Measure `Net Profit` -> Financial
- **GOOD:** Measure `YoY Growth %` -> Time Intelligence
- **BAD:** "Miscellaneous" as a category

### References
- **GOOD:** Referenced Measures: "Revenue, Cost"
- **GOOD:** Referenced Columns: "'Sales'[Amount], 'Date'[Year]"
- **BAD:** "All columns used" (too vague)

---

## Integration with Power BI Governance

### Regular Updates
1. **Monthly:** Refresh the Excel catalog from TMDL
2. **When changes occur:** Update affected measure markdown files
3. **Quarterly:** Review status and ownership

### Responsibilities
- **Tech Owner:** DAX, references, technical details
- **Business Owner:** Business meaning, interpretation, filter dependencies
- **Data Steward:** Catalog coordination, quality assurance

---

## Example: Measure Average Days to Ship - YoY

### From TMDL:
```
Name: Average Days to Ship - YoY
DAX: CALCULATE([Average Days to Ship], 'Time Intelligence'[Time Intelligence] = "YoY")
DisplayFolder: Shipping
FormatString: 0
Table: (implicit in measures table)
Description: Year-over-year change in Average Days to Ship
```

### In the Excel Catalog:
| Name | Description | Main Category | Referenced Measures | FormatString |
|---|---|---|---|---|
| Average Days to Ship - YoY | Year-over-year change in Average Days to Ship | Time Intelligence | Average Days to Ship | 0 |

### In Markdown (M_Average Days to Ship - YoY.md):
- Measure Group: [Average Days to Ship](...)
- DAX: [Code Block]
- Technical Description: [complete]
- Business Description: [with interpretation]
- Used Measures: Average Days to Ship
- Filter Dependencies: Time period, region, etc.

---

## Common Errors & Prevention

| Error | Consequence | Prevention |
|---|---|---|
| Invented descriptions | Incorrect governance | Derive only from code/model |
| Incomplete references | Incorrect dependencies | Document all explicit references |
| Wrong categorization | Hard to read for users | Clear categories, consistency check |
| Missing business owner | No accountability | Clarify ownership early |
| Manual Excel errors | Data inconsistency | Generate Excel from TMDL export |

---

## Tools & Automation

### Recommended
- **TMDL Export:** Power BI Desktop -> TMDL directory
- **PowerShell:** Automated parsing from TMDL to CSV
- **Excel:** Structured catalog management
- **Cowork Skills:** Automate repeated cataloging
- **Markdown:** Individual measure details for complex measures

### Optional
- DAX Studio for query analysis
- Power BI Analyzer for dependency mapping
- GitHub for version control of catalogs

---

## Next Steps

1. **Export TMDL** from the current Power BI Desktop model
2. **Create the Excel catalog** with structure and rules from this document
3. **Document critical measures** with [Data Catalog/Measures/_template_measure_documentation.md](Data Catalog/Measures/_template_measure_documentation.md)
4. **Run quality review** against the guardrails
5. **Assign owners** and integrate into the governance process

