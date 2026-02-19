# Data Dictionary

This document defines the columns in `volve_catalog_master.csv`.

## path
Original dataset location in the Volve release.

## name
Filename extracted from the dataset.

## category_raw
Original folder classification from the Volve directory structure.

## bucket
Normalized data category grouping similar data types.

## well
Canonical interpreted well identifier.

## Well Name Standardization
Well names are normalized to Norwegian Continental Shelf format:

15_9_19A → 15/9-19A

The `well` column represents the canonical well identifier used throughout the index.

## tags
Functional meaning of the file.

Examples:
CBL — cement evaluation evidence  
DDR — daily drilling report  
DLIS — wireline log container  
LWD/MWD — drilling telemetry

## record_id
Stable unique identifier derived from canonical path after deduplication.

## ext
Original file extension.

## ext_norm
Normalized lowercase extension used for querying.
