---
title: 2_Intro_to_C_Programming
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
# 2.1 Introduction
- Introducing important features of C
- Ch.3 and Ch.4 will cover C structured programming
- Programming in C securely is the gist!

# 2.2 Priting text, a simple program 

- comments: for documentation
- Functions: Perform action and makes decision = Action-decision model

Example

```C++
// Comments = readability and documentations, ignored by compiler so no outputting machine-language obj code
// We prefer this single-lined comment since shorter and less error prone

/*
Multi-line comments are like this
*/

// = To include contents of standard input output header (e.g. printf). More about this in Ch.5
#include <stdio.h> // Pre-processor directive, header file is processed pre-compiling

int main (void) { // One function must be "main" // int = return value is int // void = no input params
    printf("welcome to C \n"); // f = formatted ; = statement terminator
}
```
- Escape chars:
    - `\n` = New line
    - `\t` = Horizontal tab
    - `\a` = Alert sound/ visable alert
    - `\\` = Backslash raw string (since just `\` is part of an escape char)
    - `\"` = Double quote raw string

## Linker and Executables
1. Standard lib function (i.e. `printf` & `scanf`), compiler cannot identify spelling error, linker can!
2. Linker locates lib f(x) and insert calls into the object program . That's why Linker = executable

# 2.3 Adding 2 ints, a simple program