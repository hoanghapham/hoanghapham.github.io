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

The first step is to create a column containing the previous state, and a "row index" column. We will use the `previous_state` field to determine the point where the device switch to a new state, and use the `idx` field to generate the run-length ID.

```sql
select
    *
    , lag(state, 1) over (partition by device_id order by timestamp) as previous_state
    , row_number() over (order by timestamp) as idx
from test.consecutive_runs
order by device_id, timestamp
```

![](/generate-run-length-id-with-sql/ex1-01.png)

Since we have multiple devices, we have to `partition by device_id` when using `lag()` to make sure we do not get the state of a device into data of another device.

Next, we will check for the "switch point". If an event is a switch point, we will make the `idx` of that event NULL. This is to prepare for the generation of run-length ID.

```sql
with base as (
    select
        *
        , lag(state, 1) over (partition by device_id order by timestamp) as previous_state
        , row_number() over (order by timestamp) as idx
    from test.consecutive_runs
    order by device_id, timestamp
)

select
    *
    , case 
          when previous_state is null or state != previous_state 
          then idx 
      else null end as switch_points
from base
```

![](/generate-run-length-id-with-sql/ex1-02.png)

As you can see, row 1 (start of the event series), row 3, row 7 and row 11 are marked as the "switch points". Next we can use the IDs at these switch points to fill the NULL rows below, up to the next switch point. This forward-filling feature can be achieved by BigQuery's `last_value()` function: 

```sql
with base as (
    select
        *
        , lag(state, 1) over (partition by device_id order by timestamp) as previous_state
        , row_number() over (order by timestamp) as idx
    from test.consecutive_runs
    order by device_id, timestamp
)

, switching as (
    select
        *
        , case 
            when previous_state is null or state != previous_state 
            then idx 
        else null end as switch_points
    from base
)

select 
    *
    , last_value(switch_points ignore nulls) over (order by timestamp) as run_length_id
from switching

```

![](/generate-run-length-id-with-sql/ex1-03.png)
![](/generate-run-length-id-with-sql/ex1-04.png)

So that's how we have our run-length IDs. Now we can check on average how long does each run last:

```sql
...

, aggr as (
    select 
        device_id
        , run_length_id
        , timestamp_diff(max(timestamp), min(timestamp), second) / 60 as session_duration
    from run_length_table
    group by 1, 2
)

select 
    device_id
    , avg(session_duration) as average_session_duration
from aggr
group by 1
```

![](/generate-run-length-id-with-sql/ex1-05.png)


## Other applications of this technique

This technique can have multiple applications, for example:
- You have records user traffics on your website, but you are not happy with your tracker's default session grouping. You may want to generate the sessions by manipulating the data.
- Your have a complex web application, and you have a specific workflow that you want users to go through. You may want to group user's actions into workflows, and check the ratio of finished over unfinished workflows, and find the drop-off points to optimize your UI/UX.

Hope that this simple tutorial can give you ideas to solve these kinds of problem.