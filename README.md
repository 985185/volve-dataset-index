[![Release](https://img.shields.io/github/v/release/985185/volve-metadata-index?label=release)](https://github.com/985185/volve-metadata-index/releases)
[![License](https://img.shields.io/github/license/985185/volve-metadata-index)](LICENSE)
[![Dataset](https://img.shields.io/badge/dataset-Equinor%20Volve-lightgrey)](https://www.equinor.com/energy/volve-data-sharing)

# Volve Metadata Discovery Index

This repository provides a **research discovery index** for the public Equinor Volve field dataset.
It does **not** contain any original Volve data files.

The catalog references file paths within the official public Volve data release and does not redistribute or replicate the dataset contents.

The goal is to help researchers quickly locate usable files (logs, reports, WITSML, seismic, images) within the very large and inconsistently structured public release.

---

## Frozen Catalog Download

The full metadata catalog is provided as a frozen research artifact in **Releases → v1.0**.

Download:
**`volve_catalog_v1.zip`**

Inside the archive you will find:

`volve_catalog_v1.csv`

Open this file in Excel, Python, R, or MATLAB.

---

## What this project is

A filesystem catalog mapping:

* well association
* normalized category (bucket)
* interpreted tags (e.g., DLIS, WITSML, DDR, cement evaluation candidate)
* dataset path
* file extension

---

## What this project is NOT

This repository:

* does not host Equinor data
* does not redistribute proprietary content
* does not alter the Volve dataset
* does not validate engineering quality of files

It is a navigation and discovery aid.

---

## Using the catalog

Filter the CSV by:

* `well`
* `tags`
* `ext_norm`
* `top_folder`

Examples:

* Find DLIS logs
* Locate drilling reports
* Identify WITSML telemetry
* Search cement integrity records

---

## Reliability

A manual validation study was performed to verify automated file-type tagging.

| Category                     | Samples Checked | Correct | Precision |
| ---------------------------- | --------------: | ------: | --------: |
| DLIS                         |              50 |      50 |    100.0% |
| Cement evaluation candidates |               2 |       2 |    100.0% |

No misclassifications were observed in the inspected validation set.
The catalog should be used as a discovery and navigation aid rather than a substitute for technical verification of individual files.

---

## Norwegian Offshore Directorate (NPD) Cross-Reference

| Catalog well | Official wellbore | NPDID wellbore |
| ------------ | ----------------- | -------------: |
| 15_9-F-15    | 15/9-F-15         |           6184 |
| 15_9-F-11    | 15/9-F-11         |           7078 |
| 15_9-F-1     | 15/9-F-1          |           7223 |
| 15_9-F-12    | 15/9-F-12         |           5599 |
| 15_9_19_S    | 15/9-19 SR        |           2105 |
| 15_9-F-14    | 15/9-F-14         |           5351 |
| 15_9-F-4     | 15/9-F-4          |           5693 |
| 15_9_19_A    | 15/9-19 A         |           3145 |
| 15_9-F-5     | 15/9-F-5          |           5769 |
| 15_9_19_B    | 15/9-19 B         |           3251 |

NPDID wellbore is the Norwegian Offshore Directorate's unique identifier used in the FactPages petroleum database.

---
## How to Interpret the Catalog

The Volve public data release is a filesystem archive rather than an operational database.
The catalog indexes files and their metadata; it does not directly represent field activities.

In petroleum operations, many measurements and events are stored inside multi-channel log containers (e.g., DLIS files) or embedded within reports rather than as separately named files. A single logging run may contain numerous measurements such as caliper, resistivity, formation pressure, image logs, and cement evaluation curves, all within one file.

Because the catalog operates at the filesystem level, tags indicate what can be unambiguously identified from filenames and directory context. They do not enumerate every operation performed in the field.

Therefore:

absence of a specific tag does not imply the operation was not performed

many measurements exist as channels inside DLIS logs

some operational information exists only within reports or documentation

The catalog should be used as a discovery and navigation aid to locate candidate files for analysis, not as a complete operational history of the field.

## Citation

If you use this catalog in research, please cite:

Appalla, Tejaswy (2026). *Volve Metadata Discovery Index: A validated filesystem-level catalog for navigating the Equinor Volve public dataset*. GitHub research artifact.
https://github.com/985185/volve-metadata-index

## References

Equinor. Volve Field Data Village (public dataset release).  
https://www.equinor.com/energy/volve-data-sharing

Metadata inventory used in this project:  
https://github.com/985185/volve-metadata-index

