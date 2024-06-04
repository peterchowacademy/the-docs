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

## Setting up your PS1 terminal outlooks
```bash
#--------------------
# PS1 profile setup
#--------------------
orange=$( tput setaf 166);
yellow=$( tput setaf 228);
green=$( tput setaf 71);
black=$( tput setaf 16);
blue=$( tput setaf 27);
white=$(tput setaf 15);

bold=$(tput bold);
reset=$(tput sgr0);

PS1="\[${bold}\]\n"; #Bold Fonts
PS1+="\[${white}\][\D{%Y/%m/%d %H:%M:%S}]"; #TIME
PS1+="\[${blue}\]\u";
PS1+="\[${white}\]:";
PS1+="\[${orange}\]\h";
PS1+="\[${black}\] ";
PS1+="\[${green}\]\w";
PS1+="\[${white}\] \$ ";
PS1+="\[${reset}\]";
export PS1;

```

# Setting up git (namely `.gitconfig`)

## setting git alias
```bash
[alias]
    gogogo = "!f() { git add -A && git commit -m \"$@\" && git push; }; f"
```

## setting git config email for github contributions
Just type this into your terminal, no need to source
```bash
git config --global user.email "your@email.com"
```