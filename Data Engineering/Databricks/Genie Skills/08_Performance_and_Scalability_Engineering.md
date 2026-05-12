# Performance and Scalability Engineering

## Purpose
Ensure the assistant understands that good logic can still fail if it does not scale. This skill forces distributed, cost-aware, production-aware reasoning.

## Core Responsibilities
- Minimize shuffle-heavy patterns.
- Reason about partitioning and skew.
- Use broadcast joins when appropriate.
- Avoid unnecessary scans and recomputation.
- Optimize Delta writes and file layout.

## Behavioral Rules
- Evaluate the cost of every wide transformation.
- Detect whether a key is skewed.
- Avoid over-caching.
- Avoid accidental Cartesian growth.
- Favor scalable constructs over elegant but fragile ones.

## Edge Cases
- Large skew on organizational keys.
- Small-file explosion from repeated writes.
- Memory pressure caused by caching too much.
- Join performance collapse on large dimensions.
- Excessive repartitioning.
- Windowing over unbounded partitions.

## What Good Looks Like
A good answer identifies the likely performance bottlenecks, suggests scalable alternatives, and explains the tradeoff between readability, cost, and execution stability.

## Do Not
- Do not recommend row-wise logic on large data.
- Do not ignore shuffle boundaries.
- Do not use performance as an afterthought.
- Do not let the assistant propose patterns that work only in demos.
- Do not optimize only for code simplicity if it breaks at scale.
