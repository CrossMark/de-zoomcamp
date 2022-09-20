# Homework Week 4

## Question 1
### What is count for fhv vehicles data for year 2019?
```
SELECT COUNT(**) FROM fhv_taxi_data_external;
```

## Question 2
### How many distinct dispatching_base_num we have in fhv for 2019?
```
SELECT COUNT(DISTINCT(dispatching_base_num) FROM fhv_taxi_data_external;
```

## Question 3
### Best strategy to optimise if query always filter by dropoff_datetime and order by dispatching_base_num?
- Partition by dropoff_datetime
- Cluster by dispatching_base_num

## Question 4
### What is the count, estimated and actual data processed for query which counts trip between 2019/01/01 and 2019/03/31 for dispatching_base_num B00987, B02060, B02279?
*skipped*

## Question 5
### What will be the best partitioning or clustering strategy when filtering on dispatching_base_num and SR_Flag?
*skipped*

## Question 6
### What improvements can be seen by partitioning and clustering for data size less than 1 GB?
No improvement, or even reduced performance as the extra metadata that has to be processed outweighs the performance improvements.