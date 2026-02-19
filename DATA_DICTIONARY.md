This document describes the column structure of the Volve metadata catalog.

The catalog is distributed as a frozen research artifact:
volve_catalog_v1.csv

The file contains a metadata-only index of the official public Equinor Volve dataset and does not include any original data files.

# Data Dictionary

| Column | Description |
|---|---|
| path | Full dataset path within the Volve release |
| name | File name |
| type | File or directory |
| ext_norm | Normalized file extension |
| well | Associated well identifier |
| top_folder | Top-level directory in the dataset |
| tags | Interpreted classification labels |

## Tag examples
- DLIS: digital well logs
- WITSML: real-time drilling telemetry
- DDR_XML: drilling daily reports
- GEO_INTERP: geological interpretation files
- CBL_CANDIDATE: cement integrity related materials
