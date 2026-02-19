
# Methodology

## Catalog construction
A full filesystem traversal of the public Equinor Volve dataset was performed to generate a metadata-only index. The index records file locations and interprets file types using filename patterns, directory context, and extension normalization.

The dataset itself was not modified or copied.

## Validation of Classification Reliability

### Categories evaluated
Two high-value categories were selected:

- DLIS: Digital Log Interchange Standard well log files
- CBL_CANDIDATE: cement bond and casing integrity related files

### Sampling
A random sample of 50 entries tagged DLIS was manually inspected from 1,214 DLIS-tagged entries.

For cement evaluation, only two entries existed in the catalog. All were inspected (complete enumeration).

### Verification procedure
Each sampled record was examined using:
- filename
- directory context
- file extension

Correct classification:
- DLIS → binary .dlis well log
- CBL_CANDIDATE → cement bond / casing integrity evaluation

### Precision

| Category | Samples Checked | Correct | Precision |
|---|---:|---:|---:|
| DLIS | 50 | 50 | 100.0% |
| CBL_CANDIDATE | 2 | 2 | 100.0% |

No misclassified files were observed in the validation set.

### Interpretation
The catalog is reliable as a discovery index for locating relevant file types.  
The validation does not evaluate the engineering quality or usability of the files themselves.

### Limitations
Small populations (e.g., cement evaluation) limit statistical confidence.  
The catalog should be treated as a navigation aid rather than a replacement for technical quality control.
