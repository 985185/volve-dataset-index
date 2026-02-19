# Data Dictionary

This document defines every column in `volve_catalog_master.csv`.

## id
Internal row identifier from the catalog generation process.

## path
Original dataset path in the Volve public data release.  
This is a reference location only; the repository does not host the file.

## name
Filename extracted from the dataset.

## type
Filesystem classification (file or directory).

## category_raw
Original folder classification from the Volve dataset directory structure.

## bucket
Normalized data category assigned by the catalog to group similar data types.

Examples:
- Well_Logs_Wireline
- Drilling_Reports
- Production_Data
- Seismic
- Simulation

## well
Interpreted well association for the file.  
Derived from directory structure and filename patterns.

## tags
Interpreted functional meaning of the file.

Examples:
- CBL (cement evaluation)
- DDR (daily drilling report)
- DLIS (wireline log container)
- PLT (production logging tool)
- LWD_MWD (drilling telemetry)

Tags are intended for dataset discovery, not petrophysical interpretation.

## event_key
Grouping identifier used to associate related files belonging to the same operational event.

## record_id
Stable unique identifier derived from canonical path after mirror deduplication.

## ext
Original file extension from dataset.

## ext_norm
Normalized lowercase extension used for consistent querying.
