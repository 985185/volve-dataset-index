# QUICKSTART

This repository provides a **metadata-only discovery index** for the public Equinor Volve dataset.
It does **not** contain any Volve data files.

The goal is to help you find *where* relevant files are (logs, reports, WITSML, seismic, images) without spending days browsing folders.

---

## 1) Download the frozen catalog (v1.0)

1. Go to **Releases → v1.0**
2. Download: `volve_catalog_v1.zip`
3. Extract it to get: `volve_catalog_v1.csv`

---

## 2) Open the catalog

The catalog is a CSV with these key columns:

- `path` — dataset path to the file in the official Volve release
- `name` — filename
- `ext_norm` — normalized extension (e.g., `dlis`, `las`, `pdf`, `xml`, `segy`)
- `well` — associated well identifier (e.g., `15_9-F-11`)
- `top_folder` — high-level dataset folder grouping
- `tags` — interpreted labels (e.g., `DLIS`, `WITSML`, `DDR_XML`, `DOCS`)

See `DATA_DICTIONARY.md` for full definitions.

---

## 3) Common tasks (Excel / GUI)

### A) “Which wells have DLIS logs?”
1. Filter `tags` contains `DLIS`
2. Pivot table:
   - Rows: `well`
   - Values: `name` (count) or `path` (count)

### B) “Where are the drilling telemetry (WITSML) files?”
1. Filter `tags` contains `WITSML`
2. Sort by `well`
3. Use `path` to locate the files in the dataset release

### C) “Which wells have drilling reports?”
1. Filter `tags` contains `DDR_XML` (and/or likely DDR-related tags you use)
2. Pivot by `well`

### D) “Find cement / integrity related items”
1. Filter `tags` contains `CBL_CANDIDATE`
2. Inspect `name` and `path` for context

---

## 4) Common tasks (Python examples)

> These examples assume `volve_catalog_v1.csv` is in your current folder.

### A) Load and inspect
```python
import pandas as pd

df = pd.read_csv("volve_catalog_v1.csv", low_memory=False)
print(df.columns)
print(df.head(3))
