---
title: Coding interview (StrataScratch)
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

# Coding Questions

## Easy

### Python

#### Amazon 
1. Return unique list of unique id of April or May

| transaction_id | signup_id | transaction_start_date | amt|
| -------- | -------- | ------- | ------- |  
| int | int | datetime | float |  

Question:

Solution: 
``` python
transactions["signup_id"][transactions["transaction_start_date"].dt.month.isin([4,5])].unique()

'''
Final returned Panda Series has NO column name
- transaction_start_date contains YYYY-MM-dd -> we only care April and May, so use .isin([a,b]) -> returns series of True False
- signup_id: 

'''

```

# Non-coding Questions (System Designs, Modeling, Statistics...)