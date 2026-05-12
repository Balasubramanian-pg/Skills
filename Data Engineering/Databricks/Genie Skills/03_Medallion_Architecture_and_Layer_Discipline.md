# Medallion Architecture and Layer Discipline

## Purpose
Define where logic belongs in the architecture and prevent leakage between layers. This is what keeps the system governable and understandable.

## Architecture View
The Medallion Architecture should function as a controlled trust progression:
- Bronze preserves raw source truth.
- Silver standardizes, reconciles, deduplicates, and resolves conflict.
- Gold publishes stable business consumption outputs.

## Core Responsibilities
- Assign each transformation to the correct layer.
- Preserve source fidelity in Bronze.
- Perform reconciliation and canonicalization in Silver.
- Keep reporting logic in Gold.
- Ensure every layer has a distinct purpose.

## Behavioral Rules
- Do not mutate raw source data in Bronze.
- Do not hide business rules inside Gold reporting logic.
- Do not place survivorship or entity resolution in the wrong layer.
- Keep Silver as the domain of controlled transformation and trust-building.
- Make layer transitions explicit and auditable.

## Edge Cases
- Cleansing logic accidentally embedded in Gold.
- Survivorship logic split across multiple notebooks.
- Raw ingestion silently overwritten.
- Business rule changes requiring historical reprocessing.
- Data quality checks placed too late to prevent contamination.
- Crosswalk logic duplicated in multiple layers.

## What Good Looks Like
A good answer identifies the proper layer for each rule and explains why the architecture should preserve traceability from raw ingestion to consumption output.

## Do Not
- Do not mix ingestion, reconciliation, and reporting concerns.
- Do not collapse Silver into an undefined staging area.
- Do not move business logic into the wrong layer for convenience.
- Do not let architectural boundaries become vague.
