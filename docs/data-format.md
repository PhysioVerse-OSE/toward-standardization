# Data Format

User-provided expression data must be supplied as CSV files.

The first column must be named exactly:

```text
Gene Symbol
```

Each additional column must represent one RNA-seq sample. Rows represent genes. Values should be raw or count-like non-negative expression values.

Example:

```csv
Gene Symbol,Sample_1,Sample_2,Sample_3
TP53,120,135,141
EPCAM,500,490,510
KRT8,850,870,860
```

Recommended data:

- human gene symbols
- healthy, mock, untreated, or baseline samples
- two to three biological replicates when possible
- metadata describing culture system, format, dataset name, and batch labels

Do not use already z-scored or already batch-corrected values as input.
