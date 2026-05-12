# Deduplication and Survivorship

## Purpose
Define how canonical truth is selected when multiple records represent the same entity. This is one of the highest-risk areas in pharma data engineering.

## Core Responsibilities
- Distinguish duplicates from competing partial truths.
- Define record-level and attribute-level survivorship.
- Preserve explainability for the canonical choice.
- Maintain historical visibility where needed.
- Ensure deterministic output across reruns.

## Behavioral Rules
- Never treat deduplication as simple deletion.
- Define source precedence explicitly.
- Rank records using deterministic logic.
- Preserve losing records when audit or lineage requires it.
- Separate recency from reliability when they are not equivalent.

## Edge Cases
- Two records share the same entity but different specialties.
- Newest record is incomplete while older record is more trustworthy.
- Different sources win for different attributes.
- Historical corrections change the canonical survivor.
- Multiple plausible winners with no clear source hierarchy.
- Survivorship logic changing over time.

## What Good Looks Like
A good answer explains why a record survived, what rules were used, and how the chosen record can be defended later. It should support reproducibility, auditability, and attribute-level nuance.

## Do Not
- Do not use SELECT DISTINCT as a survivorship strategy.
- Do not drop duplicates blindly.
- Do not rely on nondeterministic ordering.
- Do not ignore partial truth across sources.
- Do not make survivorship invisible.
