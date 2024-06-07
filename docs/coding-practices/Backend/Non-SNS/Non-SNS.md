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
Page: refers to row entries, collapsable and able to have children <br/>
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
3. Basics: Header(s) -> Key=Authorization -> Value=secret_xxxxxxxxxxx <br/> (**Internal Integration secret**)
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

## Setup up using [Spring Initializr](https://start.spring.io) and basic config setup
1.Head over to [Spring Initializr](https://start.spring.io)
2.Make sure you have the following specs:
- Project type/ Build automation tool: Maven (repository)
- Language: Java
- Spring boot version: 3.3.0

Project metadata:

- Group (usually company domain):com.edamame
- Artifact(usually company project name): notion
- Name: swag
- Description: `Spring Boot Project for setting up RESTApi for notion deployed through github pages`
- Package name: default is com.edamame.notion 
- Packaging type: jar
- Java version: 22


Dependencies:

- Lombok: Helps to reduce writing boilerplate code
- Spring Web: Building RESTful apc with MVC
- Spring Configuration Processor: Able to custom configing keys
- Spring Data JPA: Persisting data wuth Java persistence API w/ Spring Data & Hibernate 

3.Unzip the generated zip, put everything into the local dirs try running `mvn clean install -Dmaven.test.skip=true`to ensure a correct build and commit to github

If you have not setup Maven locally yet, please refer to this [guide](/docs/coding-practices/Terminal/My-attempts-and-notes/My-attempts-and-notes.md) and find Setting up maven

4.Download 2 extensions
- Extension Pack for Java
- Spring Boot Extension Pack

Enable Null annotation type

Setting -> Workspace -> Check (Editor: format On Save)

5.Add a dir under .../notion (same level as your Application.java)
and add a file `NotionConfigProperties.java`

Add in String params
And use @ConfigurationProperties so that the devs can access by notion.apiVersion ...

Please beware that this is a record not a java class
{:.warning}

This is a **Bean**

```java
package com.edamame.notion.config;

import org.springframework.boot.context.properties.ConfigurationProperties;

@ConfigurationProperties(prefix = "notion")
public record NotionConfigProperties(String apiUrl, String apiVersion, String authToken, String databaseId) {
}

```

Run `mvn clean install -Dmaven.test.skip=true`to build the project once and then you will be able to access the params in applcaition.properties

6.Head back to the Application.java
add in the annotation

This is our **Main Method File**

```java
package com.edamame.notion;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.boot.context.properties.EnableConfigurationProperties;

import com.edamame.notion.Config.NotionConfigProperties;

@SpringBootApplication
@EnableConfigurationProperties(NotionConfigProperties.class)
public class SwagApplication {

	public static void main(String[] args) {
		SpringApplication.run(SwagApplication.class, args);
	}

}

```

7.Add a new file `secrets.properties` next to application.properties
```java
notion.auth-token=
```

8.Update your application.properties into the following:

```java
spring.application.name=swag
spring.config.import=optional:secrets.properties
notion.api-version=2022-02-22
notion.api-url=https://api.notion.com
notion.database-id=5fe3f5c9-4740-495b-9d25-e204077b9d00
```

9.Add the following to .gitignore

```
#secrets file not to be committed
secrets.properties
```

10.Also please set up the final folder structure

src/main/java/com/aaa/bbb
------------------------------
|
|-- controller/
|-- model/
|-- notion/
    |
    |--- config/
    |--- model/
    |--- service/
    |--- SwagApplication.java


