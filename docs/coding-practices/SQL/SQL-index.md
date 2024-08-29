---
title: SQL
layout: default
parent: Coding Practices 
has_children: true
---

# Non-SNS
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
# Terminology
1. SSMS: Microsoft's SQL Server Management Studio (we're using 17)
2.  


# Basics

## Hierarchy
**Server** > SQL Server Agent | **Database(s)** > View | **Table(s)** | Programmability > **Column(s)** | Keys | Indexes | Constraints

## Removing a table
```SQL
TRUNCATE TABLE [Database Name].[dbo].[Table Name]

```

## Removing a row entry from a table
```SQL
DELETE [Database Name].[dbo].Table_Name WHERE [Column1] = 'stuff1' AND [CurDate] = CONVERT(VARCHAR(8), GETDATE(), 112)

-- CurDate is matching date cases YYYYMMDD

```

## Running store proc 
```SQL
EXEC [Database Name].[dbo].[Store Proc Name] @Input1='input1', @Input2='input2'

```

# Views
## Running a View in SSMS (from Microsoft)
```bash
Right click on view -> Select Top 1000 Rows
```

## Altering a a View SSMS (from Microsoft)
```bash
Right Script View as -> ALTER To -> Edit SQL -> Top left "Execute"
```

## Altering View using techniques (i.e. CONVERT, ROUND, NUMERIC, CASE WHEN, VARCHAR, THEN, END, AS)

```SQL

```