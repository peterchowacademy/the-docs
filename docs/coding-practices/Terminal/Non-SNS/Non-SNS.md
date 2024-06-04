---
title: Non-SNS
layout: default
parent: Terminal 
grand_parent: Coding Practices
---

# Non-SNS
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Setting up bash

## Ignoring case-sensitiveness in bash during auto-completion
```bash
bind 'set completion-ignore-case on'
```

## Force tab auto-complete to cycle through options
```bash 
bind '"\t":menu-complete'
```
