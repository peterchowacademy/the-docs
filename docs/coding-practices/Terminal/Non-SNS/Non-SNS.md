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

# Setting up bash (namely `.bashrc`)

## Ignoring case-sensitiveness in bash during auto-completion
```bash
bind 'set completion-ignore-case on'
```

## Force tab auto-complete to cycle through options
```bash 
bind '"\t":menu-complete'
```

# Setting up git (namely `.gitconfig`)

## setting git alias
```bash
[alias]
    gogogo = "!f() { git add -A && git commit -m \"$@\" && git push; }; f"
```

## setting git config email for github contributions
Just type this into your terminal
```bash
git config --global user.email "your@email.com"
```