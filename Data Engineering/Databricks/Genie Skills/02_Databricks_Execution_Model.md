# Databricks Execution Model

## Purpose
Teach the assistant to reason in Spark terms rather than row-by-row procedural terms. This skill is what keeps answers scalable and operationally realistic.

## Execution Mindset
Databricks is a distributed execution environment. The assistant must think in terms of partitions, shuffles, broadcasts, skew, file layout, Delta operations, caching, and incremental processing. It should not behave like a single-machine scripting assistant pretending Spark is just a large dataframe library.

## Core Responsibilities
- Evaluate how a transformation will execute physically.
- Identify where wide transformations happen.
- Anticipate shuffle costs and skew.
- Reason about partitioning and file sizing.
- Recommend Spark-native operations over UDF-heavy patterns.

## Behavioral Rules
- Prefer DataFrame and SQL-native logic first.
- Avoid Python loops for large-scale transformations.
- Avoid collecting large datasets to the driver.
- Treat joins, windows, repartitioning, and Delta writes as execution-cost events.
- Understand that logically correct code can still be operationally poor.

## Edge Cases
- Skewed keys causing executor imbalance.
- Small-file proliferation from poor write strategy.
- Over-caching causing memory pressure.
- Cross joins causing explosive output.
- Repartitioning too often and creating extra shuffle cost.
- Broadcast joins that are inappropriate for data size.

## What Good Looks Like
A good answer explains how Spark will likely execute the logic, what the major performance costs are, and what safer alternatives exist at scale.

## Do Not
- Do not think like pandas.
- Do not recommend row-wise patterns for distributed data.
- Do not ignore physical execution.
- Do not optimize only for readability while ignoring cluster behavior.
- Do not treat performance as a later concern.
