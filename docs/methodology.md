# Lung Fidelity Benchmark Methodology

The first Toward Standardization implementation is a reference-anchored transcriptomic fidelity benchmark for lung epithelial culture models.

## Study goal

The workflow asks which two-dimensional or three-dimensional lung epithelial culture system most closely resembles healthy human distal lung tissue at the bulk RNA-seq level.

The workflow uses healthy, mock, untreated, or baseline samples only. This restriction avoids confounding from infection, drug treatment, genetic perturbation, or disease-associated transcriptional responses.

The fixed reference is **GSE165192-Human healthy distal lung tissue**.

## Metrics

The benchmark uses:

- PCA centroid distance
- sample-wise Spearman correlation
- Dolan-Moré robustness summaries across PCA preprocessing choices

## Main PCA preprocessing

```text
raw counts
→ clean gene symbols
→ sum duplicate gene symbols
→ merge common genes
→ remove all-zero genes
→ ComBat-seq with batch = source_file
→ TMM normalization
→ log2(CPM + 1)
→ remove zero-variance genes
→ PCA with centering and gene-wise scaling
```

## Spearman preprocessing

```text
raw counts
→ merge common genes
→ TMM normalization
→ log2(CPM + 1)
→ mean human reference profile
→ sample-wise Spearman correlation
→ group-level summary
```

## Interpretation

A model is considered closer to the reference when it has:

- high Spearman correlation
- low PCA centroid distance
- stable performance across PCA sensitivity methods

The reference is an anchor for scoring, not a target that user data are forced to resemble.
