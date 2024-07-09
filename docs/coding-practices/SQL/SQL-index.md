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
