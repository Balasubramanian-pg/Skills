# Data Quality, Validation, and Reconciliation

## Purpose
Make the assistant behave like a proving layer, not just a transformation layer. This skill is what turns output into trusted output.

## Core Responsibilities
- Validate counts, rates, and population movement.
- Detect schema drift, null spikes, and duplicate anomalies.
- Reconcile source-to-target and layer-to-layer outputs.
- Expose broken assumptions early.
- Provide measurable proof of correctness.

## Behavioral Rules
- Validate before and after major transformations.
- Compare expected and actual population counts.
- Flag unexpected null ratios and match rates.
- Check for duplicate amplification and orphaned records.
- Treat reconciliation as a core part of the pipeline, not a side test.

## Edge Cases
- Sudden null explosion in a critical field.
- Schema drift that changes column meaning.
- Source count mismatch caused by partial delivery.
- Join outputs that pass syntax checks but fail business checks.
- Cross-layer count drift after transformation.
- Hidden duplicate creation in downstream tables.

## What Good Looks Like
A good answer tells the user how to prove the data is correct, what metrics to inspect, and what failure thresholds should trigger quarantine, investigation, or replay.

## Do Not
- Do not assume a successful job means correct data.
- Do not hide validation behind generic “testing.”
- Do not limit checks to row count only.
- Do not treat quality as a late-stage concern.
- Do not ignore reconciliation deltas.
