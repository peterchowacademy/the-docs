---
title: 1_Intro
layout: default
parent: C++ 
grand_parent: Coding Practices
---
# Non-SNS
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# 1.1 Introduction

## Common C Compliers
1. GNU gcc complier
2. Microsoft Visual C++ complier (Complies C too)

# 1.2 Software vs Hardware
1. Software: Instructions
2. Hardware: Controlling computers
3. Moore's Law (trend): 60s Co-founder of intel said the computer power doubling while costs halved every couple of years
4. Computer terms:
- Input unit: Receving
- Output unit: Shipping
- Memory unit: RAM = primary memory
- byte = 8 bits
- bit = 1 or 0
- ALU = Arithmetic and logic Unit, imlpemented in CPU
- CPU = admin 
- Secondary storage unit = warehousing = external hard drives

# 1.3 Data Hierarchy

## From simpliest to richest
- bits: 0 or 1, short for "binary digit"
- chars: digits + letters + special symbols
    - C supports Unicode, Unicode contains 1/2/4 bytes 
    - unicode = many world languages
- fields = groups of bytes and chars = string of xxx = 1 (row) entry
- records = couple of related fields = column of the same fields (multi-entry)
- files = view = groups of related records
- database = collection of data that is easily accessible 
- big data

# 1.4 Machine language, Assembly and Assemblers, High level

All modern day programing language can be sorted into 3 types: machine code, assembly code, high level

There are 2 translator programs: 
- assembler for assembly code
- compliers for high level programming languages

## Machine Language (-> complies to 0 and 1)
1. Computers can only understand it's own machine language restricted by hardware design (Machine dependent)
2. Example:

```C++
+130042774
+1200274027
```
3. pros and cons
cons: too slow and tedious

## Assembly Code

1. Assembly languages: using eng abbr. for operations
2. Requires translator programs (aka: assemblers) to complie assembly to machine code

```bash
load    basepay
add     overpay
store   grosspay
```
## High level languages
1. 

## Interpreters
