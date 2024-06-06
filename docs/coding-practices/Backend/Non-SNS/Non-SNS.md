---
title: Non-SNS
layout: default
parent: Backend 
grand_parent: Coding Practices
---

# Non-SNS
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# 1. Setting up DB (i.e. Notion)

## Terminologies
Page: refers to row entries, collapsable and able to have children
Database: A document that is integrated with Notion API

## Set up procedures
1. Sign up an [Notion](https://www.notion.so) account
2. Head to [developers.notion.com](https://developers.notion.com), top right view my integrations
3. Add New integration and obtain Internal Integration secret token
4. Head back to [Notion](https://www.notion.so), top right click ... (right next to star icon), Connect to the new integration you just set up
5. DONE, you can now call notion API with postman