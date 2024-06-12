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
1. GET one Page/Row Entry by Page id
In the form : `https://api.notion.com/v1/pages/:id`
Must have headers: **2 in total** (Authorization & Notion-version=2022-02-22)

2. ADD/ POST one

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

```txt
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

```bash
src/main/java/com/aaa/bbb
|
|-- controller/
|-- model/
|-- notion/
    |
    |--- config/
    |--- model/
    |--- service/
    |--- SwagApplication.java
```


## Setting up <del>swagger2</del> OpenAPI 3.0

(This is due to Swagger2 doesn't work on Springboot 3.x.x applications!)
{:.warning}

0. I installed XML Red Hat VSCode extension to auto-format 

1. Add the following deps into `pom.xml`

```xml
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
    <version>2.5.0</version>
</dependency>
```

2. Create 2 files under edamame/notion/noition/model <br/>
`Database.java` and `Page.java`

Database.java
```java


// This model is what the database looks like after postman

package com.edamame.notion.notion.model;

import java.util.ArrayList;
import java.util.List;

import com.fasterxml.jackson.annotation.JsonProperty;

public class Database {
    private String object;

    @JsonProperty
    private List<Page> pages = new ArrayList<>();

    @JsonProperty("next_cursor")
    private Boolean nextCursor;

    @JsonProperty("has_more")
    private Boolean hasMore;

    public String getObject() {
        return object;
    }

    public void setObject(String object) {
        this.object = object;
    }

    public List<Page> getPages() {
        return pages;
    }

    public void setPages(List<Page> pages) {
        this.pages = pages;
    }

    public Boolean getNextCursor() {
        return nextCursor;
    }

    public void setNextCursor(Boolean nextCursor) {
        this.nextCursor = nextCursor;
    }

    public Boolean getHasMore() {
        return hasMore;
    }

    public void setHasMore(Boolean hasMore) {
        this.hasMore = hasMore;
    }

    @Override
    public String toString() {
        return "Database{" +
                "object='" + object + '\'' +
                ", pages=" + pages +
                ", nextCursor=" + nextCursor +
                ", hasMore=" + hasMore +
                '}';
    }

}

```

Page.java
```java
package com.edamame.notion.notion.model;

import com.fasterxml.jackson.annotation.JsonProperty;
import com.fasterxml.jackson.databind.JsonNode;

import java.time.LocalDateTime;

/*
 * "object": "page",
 * "id": "string",
 *  ...
 * 
 */

public class Page {

    private String object;
    private String id;
    @JsonProperty("created_time")
    private LocalDateTime createdTime;
    @JsonProperty("last_edited_time")
    private LocalDateTime lastEditedTime;
    private String cover;
    private String icon;
    private boolean archived;
    private String url;
    private JsonNode properties; // Is a dynamic list/ Dynamic json node

    public String getObject() {
        return object;
    }

    public void setObject(String object) {
        this.object = object;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public LocalDateTime getCreatedTime() {
        return createdTime;
    }

    public void setCreatedTime(LocalDateTime createdTime) {
        this.createdTime = createdTime;
    }

    public LocalDateTime getLastEditedTime() {
        return lastEditedTime;
    }

    public void setLastEditedTime(LocalDateTime lastEditedTime) {
        this.lastEditedTime = lastEditedTime;
    }

    public String getCover() {
        return cover;
    }

    public void setCover(String cover) {
        this.cover = cover;
    }

    public String getIcon() {
        return icon;
    }

    public void setIcon(String icon) {
        this.icon = icon;
    }

    public boolean isArchived() {
        return archived;
    }

    public void setArchived(boolean archived) {
        this.archived = archived;
    }

    public String getUrl() {
        return url;
    }

    public void setUrl(String url) {
        this.url = url;
    }

    public JsonNode getProperties() {
        return properties;
    }

    public void setProperties(JsonNode properties) {
        this.properties = properties;
    }

    @Override
    public String toString() {
        return "Page{" +
                "object='" + object + '\'' +
                ", id='" + id + '\'' +
                ", createdTime=" + createdTime +
                ", lastEditedTime=" + lastEditedTime +
                ", cover='" + cover + '\'' +
                ", icon='" + icon + '\'' +
                ", archived=" + archived +
                ", url='" + url + '\'' +
                ", properties=" + properties +
                '}';
    }
}

```

3. Then create a database service under /service

This service talks to the notionAPI and get the pages back <br/>
Some tips to follow, use log, use Constructor injection to get NotionConfigProperties into DatabaseService <br/>
`this.xxx = xxx` is also known as using construction arguemnts <br/>
The use of RestTemplates is to call the notion API!


```java
// This talks to the notion API and gets the pages back

package com.edamame.notion.notion.service;

import java.util.List;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.http.HttpEntity;
import org.springframework.http.HttpHeaders;
import org.springframework.http.HttpMethod;
import org.springframework.http.ResponseEntity;
import org.springframework.web.client.RestTemplate;

import com.edamame.notion.notion.config.NotionConfigProperties;
import com.edamame.notion.notion.model.Database;
import com.edamame.notion.notion.model.Page;

import org.springframework.stereotype.Component;

@Component
public class DatabaseService {

    private final RestTemplate restTemplate;
    private final NotionConfigProperties notionConfigProps;
    private final Logger log = LoggerFactory.getLogger(DatabaseService.class);

    public DatabaseService(RestTemplate restTemplate, NotionConfigProperties notionConfigProps) {
        this.restTemplate = restTemplate;
        this.notionConfigProps = notionConfigProps;
    }

    public List<Page> query(String databaseId) {
        String url = notionConfigProps.apiUrl() + "/v1/databases/" + databaseId + "/query";
        log.info("Querying Notion database: {}", url);
        ResponseEntity<Database> db = restTemplate.exchange(
                url,
                HttpMethod.POST,
                new HttpEntity<>(getDefaultHeaders()),
                Database.class);

        return db.getBody().getPages();
    }

    private HttpHeaders getDefaultHeaders() {
        HttpHeaders headers = new HttpHeaders();
        headers.set("Content-Type", "application/json");
        headers.set("Notion-Version", notionConfigProps.apiVersion());
        headers.set("Authorization", notionConfigProps.authToken());
        return headers;
    }
}

```  
4. I also added a new NotionConfig.java under /config

```java
package com.edamame.notion.notion.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.client.RestTemplate;

// Adding a new class for all notion configurations
@Configuration
public class NotionConfig {

    @Bean
    public RestTemplate restTemplate() {
        return new RestTemplate();
    } // This will now be made abaliable for dependency injection
}


```

5. Add a NotionClient under `.../.../notion/notion`
```java
package com.edamame.notion.notion;

import org.springframework.stereotype.Component;

import com.edamame.notion.notion.service.DatabaseService;

// This is mimicking what the javascript is doing

@Component
public class NotionClient {
    // get instance of the database service

    public final DatabaseService databases;

    // Add constructor parameter, to let user to call like cleint.databases.query()
    public NotionClient(DatabaseService databases) {
        this.databases = databases;
    }

}


```

## Moving onto another package: controller and model

1. We call it the `SwagController.java` under controller

```java

package com.edamame.notion.controller;

import org.springframework.web.bind.annotation.RestController;

import com.edamame.notion.model.Swag;
import com.edamame.notion.notion.NotionClient;
import com.edamame.notion.notion.config.NotionConfigProperties;
import com.edamame.notion.notion.model.Page;
import com.edamame.notion.service.SwagService;

import org.springframework.web.bind.annotation.RequestMapping;

import java.util.List;

import org.springframework.web.bind.annotation.GetMapping;

@RestController
@RequestMapping("/api")

public class SwagController {

    private final NotionClient client;
    private final NotionConfigProperties notionConfigProperties;

    public SwagController(NotionClient client, NotionConfigProperties notionConfigProperties) {
        this.client = client;
        this.notionConfigProperties = notionConfigProperties;
    }

    @GetMapping("/")
    public String home() {
        return "Welcome to the API!";
    }

    @GetMapping("path")
    public List<Swag> finalAll() {
        List<Page> pages = client.databases.query(notionConfigProperties.databaseId());

        return pages.stream().map(SwagService::mapPageToTalk).toList();
    }

}

// New object: To get the list of Swags back
// 1st thing: need notionClient and with that, we need a construction parameter


// New object: To get the list of Swags back

```

2. Then we add another package: model

We call this file `Swag.java`

```java
package com.edamame.notion.model;

import java.time.LocalDateTime;


// We're matching these to our database entries from notion
public record Swag( String id, String title, LocalDateTime startDate, LocalDateTime endDate, String url, String recording){

}


```

4. Added `SwagService.java`

However, please note that the `page.xxx` is not at all correct since this configuration was based on the old notion API fields.

I have to study in depth to figure out the response difference!

```java
package com.edamame.notion.service;

import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

import org.springframework.stereotype.Service;

import com.edamame.notion.model.Swag;
import com.edamame.notion.notion.model.Page;

@Service
public class SwagService {

    public static Swag mapPageToTalk(Page page) {
        return new Swag(
                page.getId(),
                page.getProperties().get("Title").get("title").get(0).get("text").get("content").asText(),
                LocalDateTime.parse(page.getProperties().get("StartDate").get("date").get("start").asText(),
                        DateTimeFormatter.ISO_OFFSET_DATE_TIME),
                LocalDateTime.parse(page.getProperties().get("EndDate").get("date").get("start").asText(),
                        DateTimeFormatter.ISO_OFFSET_DATE_TIME),
                page.getProperties().get("URL").get("url").asText(),
                page.getProperties().get("Recording").get("url").asText());
    }

}

```

