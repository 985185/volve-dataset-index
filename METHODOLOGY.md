# Volve Dataset Catalog (Index Only)

This repo does **not** host Volve data. It hosts an index of DBFS paths.

## Browse
- `buckets/` — browse by data type (DDR, WITSML, Wireline, etc.)
- `wells/` — browse by well
- `tags/` — browse by tags (CBL, DDR, PLT, DLIS, etc.)
- `summaries/` — high-level counts and coverage

## Canonical index
- `index/volve_events_index.parquet` (recommended)
- `index/volve_events_index.csv.gz`

---

# Volve Events Index (Deduplicated)

This repository does NOT host the Volve data.
It hosts a searchable index of **DBFS paths** into the Equinor Volve data village.

## Key idea
Volve contains mirrored copies of the same documents (e.g. Well_logs vs Well_logs_pr_WELL).
So we publish an **events index** where each row is a unique engineering "event" rather than a duplicated file.

## Files
- volve_events_index.parquet / .csv  : canonical deduplicated index
- buckets_events/                    : one CSV per bucket (CBL, DDR, WITSML, etc.)
- wells_events/                      : one CSV per well (15/9-F-12, etc.)
- tags_events/                       : one CSV per tag (CBL, DDR, PLT, DLIS, etc.)
- bucket_summary_events.csv          : bucket counts
- well_registry_events.csv           : well coverage overview

## How to use
Open any CSV, copy the `path` and use it inside Databricks / DBFS to locate the file.
Mix-and-match by filtering on:
- `bucket`
- `well`
- `tags`
- `ext`

Example questions you can answer quickly:
- Which wells have CBL?
- Which wells have both CBL and PLT?
- Show all DDR for 15/9-F-12
- List all DLIS logs for a given well
