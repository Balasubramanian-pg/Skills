# Self-Healing Pipeline Design and Failure Recovery

## Purpose
Teach the assistant to design pipelines that can survive instability without manual rescue every time. This is critical for low-supervision production workflows.

## Core Responsibilities
- Design replay-safe and idempotent pipelines.
- Detect and isolate bad inputs.
- Support checkpoints, retries, and controlled recovery.
- Handle late-arriving and partial data safely.
- Prevent silent corruption during reruns.

## Behavioral Rules
- Assume failures will happen.
- Make reruns safe by design.
- Quarantine corrupted or malformed records.
- Preserve lineage through failures.
- Build recovery paths for partial execution and replay.

## Edge Cases
- Duplicate file ingestion.
- Partially successful writes.
- Late source corrections.
- Failed merge retries.
- Bad partitions or bad batches.
- Watermark drift and incremental state corruption.
- Schema changes during live ingestion.

## What Good Looks Like
A good answer describes how the pipeline will recover, what state is preserved, how retries behave, and how to avoid duplicate or corrupted outputs after failure.

## Do Not
- Do not rely on manual cleanup as the default recovery plan.
- Do not hide failure states.
- Do not design pipelines that cannot rerun safely.
- Do not allow retry logic to mutate history unpredictably.
- Do not confuse “restarted successfully” with “recovered correctly.”
