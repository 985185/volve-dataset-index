# QUICKSTART

This repository provides a **metadata-only discovery index** for the public Equinor Volve dataset.
It does **not** contain any Volve data files.

The goal is to help you find *where* relevant files are (logs, reports, WITSML, seismic, images) without spending days browsing folders.

---

## 1) Download the frozen catalog (v1.0)

1. Go to **Releases → v1.0**
2. Download: `volve_catalog_v1.zip`
3. Extract it to obtain:

```
volve_catalog_v1.csv
```

---

## 2) Open the catalog

The catalog is a CSV with these key columns:

* `path` — dataset path to the file in the official Volve release
* `name` — filename
* `ext_norm` — normalized extension (e.g., `dlis`, `las`, `pdf`, `xml`, `segy`)
* `well` — associated well identifier (e.g., `15_9-F-11`)
* `top_folder` — high-level dataset folder grouping
* `tags` — interpreted labels (e.g., `DLIS`, `WITSML`, `DDR_XML`, `DOCS`)

See `DATA_DICTIONARY.md` for full definitions.

---

## 3) Common tasks (Excel / GUI)

### A) Which wells have DLIS logs?

1. Filter column `tags` contains `DLIS`
2. Create a pivot table:

   * Rows → `well`
   * Values → `name` (count)

### B) Where are the drilling telemetry (WITSML) files?

1. Filter `tags` contains `WITSML`
2. Sort by `well`
3. Use `path` to locate the files in the dataset release

### C) Which wells have drilling reports?

1. Filter `tags` contains `DDR_XML`
2. Pivot by `well`

### D) Find cement / integrity related items

1. Filter `tags` contains `CBL_CANDIDATE`
2. Inspect `name` and `path` for context

---

## 4) Common tasks (Python examples)

> Assumes `volve_catalog_v1.csv` is in the working directory.

### A) Load and inspect

```python
import pandas as pd

df = pd.read_csv("volve_catalog_v1.csv", low_memory=False)
print(df.columns)
print(df.head(3))
```

### B) Count files per well

```python
df["well"].value_counts().head(20)
```

### C) Find all DLIS files

```python
dlis = df[df["tags"].fillna("").str.contains("DLIS")]
dlis[["well","ext_norm","name","path"]].head(20)
```

### D) Wells that have any DLIS

```python
sorted(dlis["well"].dropna().unique())[:30]
```

### E) Find WITSML telemetry

```python
w = df[df["tags"].fillna("").str.contains("WITSML")]
w[["well","name","path"]].head(20)
```

### F) Build a quick coverage matrix (well × tag)

```python
tmp = df.copy()
tmp["tags_norm"] = tmp["tags"].fillna("")
tmp = tmp.assign(tag=tmp["tags_norm"].str.split("|")).explode("tag")
tmp["tag"] = tmp["tag"].str.strip()
tmp = tmp[tmp["tag"] != ""]

coverage = (
    tmp.groupby(["well","tag"])
       .size()
       .reset_index(name="count")
       .sort_values(["well","count"], ascending=[True, False])
)

coverage.head(30)
```

---

## 5) Important interpretation note (read once)

The Volve public release is a **filesystem archive**, not an operational database.

Tags indicate what can be **unambiguously identified from filenames and directory context**.
They do **not** enumerate every operation performed in the field.

Therefore:

* absence of a tag does not imply the operation was not performed
* many measurements exist as channels inside DLIS logs
* some operational information exists only within reports and documentation

Use the catalog to locate candidate files for analysis, not as a complete operational history.

---

## 6) Citation

See `README.md` for the recommended citation text.
