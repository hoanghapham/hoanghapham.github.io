---
title: "Generate Run-Length ID With SQL"
date: 2022-02-07T20:42:18+07:00
draft: true
---

- Content:
    - What is run-length encoding & run-length ID
    - What is its use case in business?
    - How is it implemented in other languages?
    - Implement it in SQL
        - Sample use case (Business Question)
        - Shape of source data
        - Desired outcome
        - Step-by-step guide

# What is run-length ID?

Sometimes during analysis work, you need to group **consecutive sequence of values** into different "runs", and calculate metrics for each run. For example:

- Given a time series recording some object's state, you want to calculate on average, how long does an object stay in a particular state.
- Or a more specific example: Given a series of event data of several users, you want to group the users' events into sessions with a session cut-off threshold of your choice

(Image of rows recording consecutive runs)

# Generate run-length ID with R

If you are an R user, you may have heard of this kind of analysis. This operation is made trivial with the `data.table` package, since its `rleid`/`rleidv` function can directly generate **run-length IDs** that are incremented when a new run is commenced.

(Image of R's `rleid`)

In this post, I will walk you through the steps to generate the same run-length IDs using SQL. I will use BigQuery's Standard SQL to demonstrate it, but you can implement this as long as your SQL support window functions (LEAD, LAG, ROW_NUMBER...).

# Generate run-length ID with SQL

## Example: How long do they stay in a state?
- Suppose we have a record of users going different states when interacting with our business (state 1, state 2, state 3, state 2, state 3, state 4)... 
- We want to calculate how long do they typically stay in a certain state



## Example: Generate your own session ID
- Suppose we have a record of users' events on our website
- We are not happy with the default session cut-off threshold, and we want to use SQL to generate our own session
