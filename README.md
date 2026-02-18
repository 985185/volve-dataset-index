# Volve Field Dataset --- Research Catalog (Metadata Index)

This repository is NOT a copy of the Equinor Volve dataset.

It is a searchable metadata index of the public Volve field dataset
designed to help researchers understand what data exists before
attempting analysis or machine learning.

The real Volve dataset contains \~400,000 files across multiple
inconsistent folder structures and formats. Researchers commonly spend
days or weeks manually locating relevant logs, drilling reports, and
production information.

This catalog solves that problem.

------------------------------------------------------------------------

## What this repository provides

For every file in the public Volve dataset, this index records:

-   well (when determinable)
-   data bucket (data type category)
-   tags (CBL, DDR, DLIS, PLT, etc.)
-   file path
-   file extension
-   derived properties

The repository does NOT host or redistribute any proprietary data. It
only describes the dataset structure.

------------------------------------------------------------------------

## Why this matters

Typical research questions that are difficult to answer using the raw
dataset:

-   Which wells have cement bond logs?
-   Which wells contain daily drilling reports?
-   Where are the DLIS wireline logs?
-   Which wells have production logging (PLT)?
-   What data exists before building ML models?

This catalog allows those questions to be answered instantly.

------------------------------------------------------------------------

## Repository structure

### Master Index

`volve_catalog_master.csv`

Complete metadata table of the dataset.

### Per Well

`/per_well/` Each CSV contains all files associated with a single well.

### Per Bucket

`/per_bucket/` Files grouped by data type.

### Per Tag

`/per_tag/` Files grouped by interpreted meaning.

------------------------------------------------------------------------

## Tag definitions

  Tag       Meaning
  --------- -----------------------------------------------------
  CBL       Cement Bond Log / cement evaluation evidence
  DDR       Daily Drilling Report
  DLIS      Digital Log Interchange Standard wireline log
  PLT       Production Logging Tool
  LWD/MWD   Logging While Drilling / Measurement While Drilling
  PDS       Landmark/OpenWorks plot file
  PLOT      Graphical log panel

Important: Cement evaluation evidence may exist as DLIS logs, ASCII
exports, PDF reports, or Landmark PDS plot files.

------------------------------------------------------------------------

## Known limitations

### Production Data

The production dataset uses PI system instrument identifiers rather than
wells. These represent facility sensors, not well names. Mapping to
wells requires an external mapping table not included in the public
release.

### Sparse Wells

Some wells contain very few files. This reflects archival availability
in the public dataset, not an indexing error.

### Tagging Method

Tags are assigned using filename patterns, folder context, and file
types. They are intended to assist dataset discovery and may not
represent full petrophysical interpretation.

------------------------------------------------------------------------

## How to cite

If you use this catalog in research, please cite:

"Volve Field Dataset Research Catalog (Metadata Index), GitHub
repository."

------------------------------------------------------------------------

## Intended use

This repository is designed to support:

-   petroleum engineering research
-   drilling analytics
-   machine learning dataset preparation
-   reproducible Volve field studies

It provides a reproducible way to determine data availability before
analysis.

------------------------------------------------------------------------

## Dataset source

The underlying dataset is publicly released by Equinor:
https://www.equinor.com/energy/volve-data-sharing
