---
title: Coding interview (StrataScratch)
layout: default
parent: Coding Practices
has_children: true
---
# Non-SNS
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Coding Questions

## Easy

### Python

#### Amazon - Return unique list of unique id of April or May

| transaction_id | signup_id | transaction_start_date | amt|
| -------- | -------- | ------- | ------- |  
| int | int | datetime | float |  

Question:

Solution: 
``` python
transactions["signup_id"][transactions["transaction_start_date"].dt.month.isin([4,5])].unique()

'''
Final returned Panda Series has NO column name
- transaction_start_date contains YYYY-MM-dd -> we only care April and May, so use .isin([a,b]) -> returns series of True False in the second []
- signup_id: is the target final column to be returned 
- unique(): returns only unique value + reset column name

'''

```

#### Spotify - Aggregate Listening Data (ID: 10367)

| user_id | song_id | listen_duration | 
| -------- | -------- | ------- | 
| int | int | float |

Question: Capture spotify user habits
- Per user, find the total listening time and the count of unqiue songs they listen to
- return total listening time as min not seconds
- return columns should be: user_id, total_listen_duration, unique_song_count

Solution: 

- First set all missing listening duration to 0
- set all exisiting listening duration to nearest min

``` python


'''
Final returned Panda Series has NO column name
- transaction_start_date contains YYYY-MM-dd -> we only care April and May, so use .isin([a,b]) -> returns series of True False in the second []
- signup_id: is the target final column to be returned 
- unique(): returns only unique value + reset column name

'''

```


# Non-coding Questions (System Designs, Modeling, Statistics...)