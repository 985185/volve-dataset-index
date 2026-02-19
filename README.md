
# Volve Metadata Discovery Index

This repository provides a **research discovery index** for the public Equinor Volve field dataset.  
It does **not** contain any original Volve data files.

The goal is to help researchers quickly locate usable files (logs, reports, WITSML, seismic, images) within the very large and inconsistently structured public release.

## What this project is
A filesystem catalog mapping:
- well association
- normalized category (bucket)
- interpreted tags (e.g., DLIS, WITSML, DDR, cement evaluation candidate)
- dataset path
- file extension

## What this project is NOT
This repository:
- does not host Equinor data
- does not redistribute proprietary content
- does not alter the Volve dataset
- does not validate engineering quality of files

It is a navigation and discovery aid.

## Using the catalog
Open `volve data meta.csv` in Excel, Python, R, or MATLAB and filter by:

- `well`
- `tags`
- `ext_norm`
- `top_folder`

Examples:
- Find DLIS logs
- Locate drilling reports
- Identify WITSML telemetry
- Search cement integrity records

## Reliability
A manual validation study was performed to verify automated file-type tagging.

- DLIS: 50/50 correct in a random sample
- Cement evaluation candidates: 2/2 correct (complete enumeration)

No misclassifications were observed in the inspected validation set.  
The catalog should be used as a discovery and navigation aid rather than a substitute for technical verification of individual files.

## Norwegian Offshore Directorate (NPD) cross-reference
Top wells mapped to official wellbore identifiers:

| Catalog well | Official wellbore | NPDID wellbore |
|---|---|---:|
| 15_9-F-15 | 15/9-F-15 | 6184 |
| 15_9-F-11 | 15/9-F-11 | 7078 |
| 15_9-F-1 | 15/9-F-1 | 7223 |
| 15_9-F-12 | 15/9-F-12 | 5599 |
| 15_9_19_S | 15/9-19 SR | 2105 |
| 15_9-F-14 | 15/9-F-14 | 5351 |
| 15_9-F-4 | 15/9-F-4 | 5693 |
| 15_9_19_A | 15/9-19 A | 3145 |
| 15_9-F-5 | 15/9-F-5 | 5769 |
| 15_9_19_B | 15/9-19 B | 3251 |

NPDID wellbore is the Norwegian Offshore Directorate's unique identifier used in the FactPages petroleum database.

## Required file
Frozen catalog availability

The full metadata catalog associated with this study is provided as a frozen research artifact in the repository Releases section (v1.0). The repository itself contains documentation describing the catalog structure and validation procedure.

