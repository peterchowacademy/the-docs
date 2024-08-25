---
title: Data Structures
layout: default
parent: Coding Practices
has_children: true
---
# Data Structures
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Algos and Data Structs for noobs

## Arrays
### Static Arrays

Static typed languages: Java, C++, C# (meaning the arrays will need allocated size and type when the array is created)
{:.note }

1. Properties of static arrays
- when array is full = no additional element can be added
- Javascript and Python DO NOT have static arrays

2. Reading from arrays

```python

A = [1,2,3]
A[i] 

```

Each element occupies 4 address 
`1 -> $0` , `1 -> $4` , `1 -> $8`

### Dyanamics Arrays