# Catalog Generation Methodology

The Volve dataset contains approximately 400,000 files with inconsistent naming, duplicated mirror folders, and incomplete well labeling.

The goal of this catalog is **dataset discovery**, not engineering interpretation.

---

## Step 1 — File inventory

All files were recursively indexed from the public dataset release.

Only metadata was recorded:
- file path
- filename
- extension
- directory structure

No file contents were modified or redistributed.

---

## Step 2 — Mirror deduplication

The dataset contains mirrored directories (e.g., `Well_logs` and `Well_logs_pr_WELL`). Duplicate entries were removed using a canonical path + stable record identifier hashing so each real file appears only once in the index.

---

## Step 3 — Well association

Well names were inferred using directory structure and filename patterns consistent with Norwegian Continental Shelf naming.

Example: `15_9_19A` → `15/9-19A`

---

## Tag assignment mechanism

Tags are assigned using deterministic, rule-based classification derived from file names, extensions, and folder context.

No manual labeling or machine learning classification was used.

### Extension-based rules
- `ext_norm == "dlis"` → `DLIS`
- `ext_norm == "las"` → `LAS`
- `ext_norm == "xml"` in drilling/telemetry folders → `LWD_MWD`
- `ext_norm == "pds"` → `PDS|PLOT`

### Keyword rules
Files whose filename or path contains:
- `daily`, `ddr`, date-formatted drilling HTML/PDF → `DDR`
- `cbl`, `cement`, `bond`, `usit`, `cmt`, `cement eval` → `CBL`

### Folder-context rules
Files located inside drilling report directories are classified as `DDR` even when filenames are inconsistent.

Tags indicate **discovery relevance**, not engineering interpretation.

---

## Known limitations

- Tagging is pattern-based and may miss files with unconventional vendor naming.
- Cement evaluation evidence may exist in plots or reports without explicit `CBL` naming.
- The catalog identifies candidate data sources; users should inspect files before detailed interpretation.

---

## Validation sample (manual QC)

A small manual audit can be performed to estimate tag precision.
Random samples should be drawn from the master index for key tags (DDR, CBL, DLIS) and checked by inspecting filenames and folder context.

This validation estimates precision (how often a tagged item is truly relevant), not recall (how many relevant items may be untagged).

(Optional — fill in once you run a quick audit)
- DDR precision: __/100 (__%)
- CBL precision: __/50 (__%)
- DLIS precision: __/100 (__%)

---

## File sizes

A full `file_size_bytes` enrichment is not included in the current release.

In shared Unity Catalog environments, per-file size lookup requires remote metadata calls and can take ~30 hours for ~400k files.
This is a compute-heavy enhancement with limited benefit for many research workflows.
