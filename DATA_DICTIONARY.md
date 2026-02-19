# Data Dictionary

This document defines the columns in `volve_catalog_master.csv`.

## id
Internal row identifier from the catalog generation process.

## path
Original dataset location in the Volve release.

## name
Filename extracted from the dataset.

## type
Filesystem classification (file or directory).

## category_raw
Original folder classification from the Volve directory structure.

## bucket
Normalized data category grouping similar data types.

## well
Canonical interpreted well identifier.

### Well normalization
The `well` column is a canonicalized identifier derived from directory structure and filename patterns.

Normalization rules include:
- converting underscores to NCS-style formatting (e.g., `15_9_19A` → `15/9-19A`)
- standardizing separators (slash + hyphen)
- trimming whitespace and removing common noise tokens

Important:
- This normalization is intended for internal consistency within this catalog.
- It is not guaranteed to match official Norwegian Offshore Directorate (FactPages) identifiers 100% without a dedicated crosswalk table.

## tags
Functional meaning of the file for discovery purposes (pipe-delimited).

Examples:
- `CBL` — cement evaluation evidence
- `DDR` — daily drilling report
- `DLIS` — wireline log container
- `LWD_MWD` — drilling telemetry indicator
- `PDS|PLOT` — plot file format indicator

## event_key
Grouping identifier used to associate related files belonging to the same operational event (where applicable).

## record_id
Stable unique identifier derived from canonical path after deduplication.

## ext
Original file extension.

## ext_norm
Normalized lowercase extension used for querying.
