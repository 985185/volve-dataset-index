# Catalog Generation Methodology

The Volve dataset contains approximately 400,000 files with inconsistent naming, duplicated mirror folders, and incomplete well labeling.

The goal of this catalog is dataset discovery, not engineering interpretation.

---

## Step 1 — File Inventory
All files were recursively indexed from the public dataset release.

Only metadata was recorded:
- file path
- filename
- extension
- directory structure

No file contents were modified or redistributed.

---

## Step 2 — Mirror Deduplication
The dataset contains mirrored directories (e.g., Well_logs and Well_logs_pr_WELL).

Duplicate entries were removed using a canonical path and record identifier hashing. Each real file appears only once in the index.

---

## Step 3 — Well Association
Well names were inferred using directory structure and filename patterns consistent with Norwegian Continental Shelf naming.

Example:
15_9_19A → 15/9-19A

---

## Tag Assignment Mechanism

Tags are assigned using deterministic rule-based classification derived from file names, extensions, and folder context.

No manual labeling or machine learning classification was used.

### Extension-based rules
- ext_norm == "dlis" → DLIS
- ext_norm == "las" → LAS
- ext_norm == "xml" in drilling folders → LWD_MWD
- ext_norm == "pds" → PDS|PLOT

### Keyword rules
Files whose filename or path contains:
- "daily", "ddr", date-formatted drilling HTML/PDF → DDR
- "cbl", "cement", "bond", "usit", "cmt", "cement eval" → CBL

### Folder context rules
Files located inside drilling report directories are classified as DDR even when filenames are inconsistent.

Tags indicate discovery relevance, not engineering interpretation.

---

## Known Limitations

- Tagging is pattern-based and may miss files with unconventional vendor naming.
- Cement evaluation evidence may exist in plots or reports without explicit CBL naming.
- The catalog identifies candidate data sources. Users should inspect files before detailed engineering analysis.
