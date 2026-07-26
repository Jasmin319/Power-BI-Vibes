# Agent Playbook: Generate Table Documentation from PBIP Semantic Model

## Purpose
This playbook defines a repeatable process to create Obsidian-ready table documentation from a Power BI PBIP semantic model.

It is designed to be transferable to any PBIP project, not only this repository.

---

## Required Inputs
1. PBIP semantic model table folder:
   - Power BI/<ModelName>.SemanticModel/definition/tables
2. Relationship file:
   - Power BI/<ModelName>.SemanticModel/definition/relationships.tmdl
3. Documentation template:
   - Data Catalog/Tables/_template_table_documentation.md
4. Measure documentation template:
   - Data Catalog/Measures/_template_measure_documentation.md
5. Measure source table:
   - Power BI/<ModelName>.SemanticModel/definition/tables/_Measures.tmdl
6. Target output folders:
   - Data Catalog/Tables/Dimensions
   - Data Catalog/Tables/Facts
   - Data Catalog/Tables (for metadata/helper tables)
   - Data Catalog/Measures

---

## High-Level Procedure

### 1. Discover model tables
1. List all .tmdl files in the semantic model tables folder.
2. Exclude non-table artifacts only if they are truly not tables.
3. Keep these table types:
   - Dimension tables (typically Dim_*)
   - Fact tables (typically Fact_*)
   - Metadata/helper tables (for example _Measures, Measure Catalog, Time Intelligence)

### 2. Read source metadata per table
For each table .tmdl, extract:
1. Table description comment (/// at top)
2. Table name
3. lineageTag
4. Columns:
   - Name
   - dataType (if present)
   - sourceColumn (if present)
   - flags: isUnique, isHidden
   - calculated expression (if column has = ...)
   - dataCategory (if present)
5. Partition/source details:
   - import/m/calculated/calculationGroup
   - source object hint (csv file, DAX expression, DATATABLE, etc.)

### 3. Build relationship map
From relationships.tmdl:
1. Parse every relationship with:
   - fromColumn: <Table>[<Column>]
   - toColumn: <Table>[<Column>]
2. For each table, compute:
   - Incoming relationships (other table points to this table)
   - Outgoing relationships (this table points to another table)
3. Write relationship references using standard Markdown links with relative file paths:
   - [Fact_Order](../Facts/Fact_Order.md)[Customer ID] -> [Dim_Customer](Dim_Customer.md)[Customer ID]

### 4. Classify output destination
Use naming + table purpose:
1. Dim_* -> Data Catalog/Tables/Dimensions/<Table>.md
2. Fact_* -> Data Catalog/Tables/Facts/<Table>.md
3. Everything else -> Data Catalog/Tables/<Table>.md

### 5. Populate template sections
Fill all template sections consistently:
1. Quick Overview
2. Table Properties (Structured Overview)
3. Column List
4. Key Overview
5. Relationships
6. Usage and Context
7. Maintenance Notes

Rules:
1. Keep markdown structure identical to template.
2. Use model-derived facts first; avoid guesses.
3. If unknown, use neutral placeholders (for example Owner: TBD).
4. Preserve human-readable business wording from table comments where possible.

### 6. Relationship link rule (reusable markdown)
In every table doc, relationship lines should use standard Markdown links (relative paths) for table names:
1. Incoming:
   - **[SourceTable](relative/path/to/SourceTable.md)[Column]** -> **[ThisTable](relative/path/to/ThisTable.md)[Column]**
2. Outgoing:
   - **[ThisTable](relative/path/to/ThisTable.md)[Column]** -> **[TargetTable](relative/path/to/TargetTable.md)[Column]**

Do not use Obsidian wikilinks (`[[Table]]`) in relationship lines.

### 7. Validate completeness
Before finishing:
1. Verify every .tmdl table has a corresponding .md file.
2. Verify each documented relationship uses relative-path Markdown links (no Obsidian wikilinks).
3. Re-read any files the user recently modified before editing them.
4. Do not overwrite unrelated user edits.

---

## Transferable Checklist (Any PBIP)
Use this checklist when starting a new PBIP project:

1. Identify semantic model root:
   - <Project>/Power BI/<Name>.SemanticModel/definition
2. Confirm these files/folders exist:
   - tables/*.tmdl
   - relationships.tmdl
3. Confirm table documentation template path.
4. Create target documentation folders if missing.
5. Generate docs for all tables.
6. Add/verify relative-path Markdown relationship links (no Obsidian wikilinks).
7. Run final coverage check: table count in tables folder vs generated docs.

---

## Conventions Used
1. Date in docs: YYYY-MM-DD
2. Owner default: TBD
3. Data type wording in docs:
   - string -> Text
   - int64 -> Integer
   - double/decimal -> Decimal
   - dateTime (date semantics) -> Date
4. Calculated columns should be marked as Derived in Column List.
5. Hidden relationship keys should be marked as Foreign Key, Hidden.

---

## Quality Bar
A table doc is complete when:
1. It follows the template structure.
2. It includes accurate column and key metadata from TMDL.
3. It includes incoming and outgoing relationships.
4. Relationship table names are linked with relative Markdown paths (no Obsidian wikilinks).
5. It is understandable without opening the original TMDL file.

---

## Measure Documentation Workflow

### 1. Discover measures
1. Read Power BI/<ModelName>.SemanticModel/definition/tables/_Measures.tmdl.
2. Parse each measure definition:
   - measure name
   - DAX expression
   - formatString
   - displayFolder
   - preceding model comment (///), if available

### 2. Create one file per measure
1. Use one markdown file per measure.
2. File naming rule:
   - M_<Measure Name>.md
   - replace invalid filename characters with underscore if needed
3. Write files to Data Catalog/Measures.

### 3. Populate from measure template
Use Data Catalog/Measures/_template_measure_documentation.md and fill these sections:
1. Measure Group
2. DAX
3. Technical Description
4. Business Description
5. References & Links
6. Change History
7. Source (Comment from Model)

### 4. Dependency extraction rules
For each measure, derive and populate:
1. Used measures:
   - references like [Other Measure]
2. Used columns:
   - references like 'Table'[Column] and Table[Column]
3. Used tables:
   - distinct tables used by column references
4. DAX functions:
   - function names from expression (for example CALCULATE, SUMX, DIVIDE)

### 5. Link rules for measure docs
Use standard Markdown links only. Do not use Obsidian wikilinks.

1. Related Measures section:
   - link to measure docs with M_ prefix
   - example: [Total Sales](M_Total Sales.md)

2. Used tables section:
   - link to table docs using paths relative to Data Catalog/Measures
   - examples:
     - [Fact_Order](../Tables/Facts/Fact_Order.md)
     - [Dim_Customer](../Tables/Dimensions/Dim_Customer.md)
     - [Time Intelligence](../Tables/Time Intelligence.md)

### 6. Validation checklist for measure docs
Before finishing:
1. Verify one file exists for each measure in _Measures.tmdl.
2. Verify all files follow M_<Measure Name>.md naming.
3. Verify Used tables links resolve to existing table .md files.
4. Verify Related Measures links resolve to existing measure .md files.
5. Verify there are zero broken markdown links in Data Catalog/Measures (excluding template/process files).

### 7. Regeneration safety
When regenerating measure docs in bulk:
1. Keep the two helper files untouched:
   - _template_measure_documentation.md
   - Measure_Documentation_Process.md
2. Re-apply link normalization after generation:
   - Related Measures -> M_ measure files
   - Used tables -> ../Tables/... paths
3. Re-check links after any rename operation.
