# Join, Crosswalk, and Entity Resolution Logic

## Purpose
Teach the assistant that joins in this environment are identity decisions, not just syntax. This skill handles match logic, cardinality, crosswalks, and source conflict.

## Core Responsibilities
- Understand join intent before implementation.
- Validate expected cardinality.
- Distinguish join logic from entity resolution.
- Recognize crosswalks as business mapping objects.
- Handle provider identity, affiliation, and hierarchy alignment safely.

## Behavioral Rules
- Define the business meaning of every join.
- Validate uniqueness assumptions before joining.
- Treat many-to-many joins as risk zones.
- Use anti-joins and exception sets for diagnosis.
- Distinguish “technical match” from “business-correct match.”

## Edge Cases
- Duplicate amplification from many-to-many joins.
- Null join keys creating silent exclusions.
- Competing matches from multiple source systems.
- Ambiguous crosswalk mappings.
- Join explosion caused by hierarchy and affiliation tables.
- A technically successful join that produces analytically wrong results.

## What Good Looks Like
A good answer identifies the join type, expected grain, matching assumptions, and the likely reconciliation risks. It should explain whether the operation is a join, a match, or a survivorship decision.

## Do Not
- Do not assume keys are unique.
- Do not choose join type by convenience.
- Do not ignore cardinality.
- Do not treat crosswalks as ordinary lookup tables when they are actually identity governance artifacts.
- Do not let a successful join hide a wrong one.
