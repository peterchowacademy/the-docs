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

# Setting up DB (i.e. Notion)

## Terminologies
Page: refers to row entries, collapsable and able to have children
Database: A document that is integrated with Notion API

## Set up procedures
1. Sign up an [Notion](https://www.notion.so) account
2. Head to [developers.notion.com](https://developers.notion.com), top right view my integrations
3. Add New integration and obtain **Internal Integration secret** token
4. Head back to [Notion](https://www.notion.so), top right click ... (right next to star icon), Connect to the new integration you just set up
5. DONE, you can now call notion API with postman

# Setting up Postman

## Set up procedures
1. Sign up [Postman](https://www.postman.com/downloads/) account
2. Fork online Notion API or write your own postman endpoints
3. Basics: Header(s) -> Key=Authorization -> Value=secret_xxxxxxxxxxx (**Internal Integration secret**)
4. Where to find database id ? Ans: 
5. Where to find page id ? Ans:

## Common endpoint offered by NotionAPI
1. Get Page/Row Entries by Page id
- 

# Setup and using Springboot

## Background/ History
1. Springboot follows an MVC (Model-view Controller) design pattern
- Model: Internal representation of data
- View: The interface for accepting user inputs
- Controller: The bridge brween Model & View

2. Springboot was released in 2014 as an improvement from Spring
- Spring packages in .war and tomcat/ Jetty server was a seperate entity (Springboot is integrated)
- Springboot offers auto-configuration (aka no need to set up xml)
- Spring is mainly for building webapps vs Springboot is mainly for building REST APIs

## Setup up [Spring Initializr](https://start.spring.io)
1. Head over to [Spring Initializr](https://start.spring.io)
2. Make sure you have the following specs:
- Project type/ Build automation tool: Maven
- Language: Java
- Spring boot version: 3.3.0
- Project metadata
    - Group:
    - Artifact:
