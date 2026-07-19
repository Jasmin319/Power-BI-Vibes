# Table Documentation Template

## Table: [Table Name]

### Quick Overview
**Role:** [e.g. Dimension, Fact, Helper table, Reference, Metadata]  
**Source:** [System/Data origin]  
**Description:** [Short description of content and purpose]  
**Last updated:** [Date]  
**Owner:** [Person/Team]  

### Table Properties (Structured Overview)

| Property | Definition |
|---|---|
| **Classification** | [Project status information / Dimension table / Fact table / Reference data] |
| **Description** | [Detailed technical description of table content and purpose] |
| **Query ID / Object ID** | [Unique technical identifier, e.g. GUID or technical name] |
| **Type** | [Fact table / Dimension table / Bridge table / Metadata table] |
| **Load-enabled** | [Yes / No] |
| **Source system** | [System/Database, e.g. ZT-Office/SQL database, SAP, Data Lake] |
| **Source object** | [Technical object name, e.g. dbo.M001_ProjectStatus, view name] |
| **Granularity** | [Granularity description: One row represents ... from a business perspective] |
| **Primary key** | [Name and explanation of the primary key] |
| **Important foreign keys** | [List of foreign keys and their targets] |
| **Business purpose** | [Description of business use case and usage] |
| **Usage for business users** | [Business purpose of the table] |
| **Special logic** | [Information about calculations, filters, or special processing rules] |
| **Usage notes** | [Special characteristics, limitations, performance notes, best practices] |

---

## Column List

| Column Name | Data Type | Property | Description |
|---|---|---|---|
| [Column 1] | [Type] | [Key/Indexed/Optional/Required] | [Description and content] |
| [Column 2] | [Type] | [Key/Indexed/Optional/Required] | [Description and content] |
| [Column 3] | [Type] | [Key/Indexed/Optional/Required] | [Description and content] |
| [Column 4] | [Type] | [Key/Indexed/Optional/Required] | [Description and content] |
| [Column 5] | [Type] | [Key/Indexed/Optional/Required] | [Description and content] |
| ... | ... | ... | ... |
| [Column n] | [Type] | [Key/Indexed/Optional/Required] | [Description and content] | 

---

## Key Overview

### Primary Key
- **Column name:** [Name of the key column]
- **Data type:** [e.g. Integer, Text, GUID]
- **Property:** [Unique, Not Null, etc.]
- **Description:** [Explanation of the key]

### Foreign Keys
| Column Name | Data Type | References | Description |
|---|---|---|---|
| [Column] | [Type] | [TargetTable.Column] | [Relationship description] |
| | | | |

---

## Relationships

### Incoming Relationships (foreign keys referencing this table)
- **[SourceTable].[Column]** -> **[This Table].[Column]**
  - Cardinality: [1:1 / 1:N / M:N]
  - Filter direction: [Single / Both]

### Outgoing Relationships (this table references others)
- **[This Table].[Column]** -> **[TargetTable].[Column]**
  - Cardinality: [1:1 / 1:N / M:N]
  - Filter direction: [Single / Both]

---

## Usage and Context

### Used Measures
- [Measure 1] - [Short description]
- [Measure 2] - [Short description]

### Reporting Context
- Dashboards/reports that use this table:
  - [Report 1]
  - [Report 2]

---

## Maintenance Notes

[Free space for notes, workarounds, performance optimizations, or future improvements]
