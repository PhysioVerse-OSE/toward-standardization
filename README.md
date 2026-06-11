# Toward Standardization

**Reference-anchored benchmarking for in vitro biological models**

Toward Standardization is a PhysioVerse open-source project focused on building transparent, reproducible workflows that help laboratories evaluate how closely an in vitro biological model reflects an appropriate declared biological reference standard.

The first implementation is a **lung epithelial culture fidelity benchmark**. It compares healthy, mock, untreated, or baseline lung epithelial culture RNA-seq profiles against a fixed healthy human distal lung tissue reference using interpretable transcriptomic fidelity metrics.

## Why this project matters

Organoids, body-on-chip platforms, organ tissue equivalents, tissue chips, and other microphysiological systems are increasingly used to model human biology. However, laboratories often need a transparent way to ask:

> How close is my model to the biological reference it is intended to represent?

This project provides a reusable framework for answering that question using declared reference datasets, shared gene-space harmonization, benchmark metrics, robustness checks, and community review.

## First implementation: lung fidelity benchmark

The current example asks:

> Which two-dimensional or three-dimensional lung epithelial culture system is transcriptomically closest to healthy human distal lung tissue?

The built-in benchmark uses public bulk RNA-seq datasets and includes:

- **GSE165192-Human** as the fixed healthy human distal lung tissue reference
- NHBE 2D primary monolayer samples
- A549 and A549-ACE2 2D immortalized monolayer samples
- Calu-3 epithelial monolayer samples
- hBEpC 2D primary monolayer samples
- hBO bronchial organoids
- ALI-HBEC differentiated epithelium
- OTE engineered airway organ tissue equivalents

The benchmark uses healthy, mock, untreated, or baseline samples only, which reduces confounding from infection, drug treatment, genetic perturbation, or disease-associated transcriptional responses.

## Core metrics

The first implementation uses two primary unsupervised metrics:

1. **PCA centroid distance**  
   Measures global transcriptomic proximity between each model group and the fixed human distal lung reference centroid.

2. **Spearman correlation**  
   Measures sample-wise gene-expression rank similarity to the mean human distal lung reference profile.

It also includes robustness summaries across PCA preprocessing choices, including a **Dolan-Moré performance profile**.

## Core principle

The reference dataset is used as an anchor for scoring, not as a target that user data are forced to resemble. The workflow reports proximity to the reference while preserving the biological identity of each model.

## Current software modes

- **Demo mode:** runs the full benchmark using the built-in lung reference database.
- **Simple user mode:** lets a user add one expression CSV and compare one new model with the built-in database.
- **Advanced user mode:** supports multiple user datasets or multiple culture-system groups with metadata.

## Input data format

User-provided expression data should be CSV files. The first column must be named exactly:

```text
Gene Symbol
```

Each remaining column should represent one RNA-seq sample. Rows represent genes. Values should be raw or count-like non-negative expression values.

Example:

```csv
Gene Symbol,Sample_1,Sample_2,Sample_3
TP53,120,135,141
EPCAM,500,490,510
KRT8,850,870,860
```

Recommended user data:

- human gene symbols
- raw or count-like values
- healthy, mock, untreated, or baseline samples
- at least two to three biological replicates when possible
- metadata describing the culture system and technical batches

Do not use already z-scored or already batch-corrected values for the benchmark input.

## What contributors can help with

We welcome contributions in several areas:

- Suggesting additional public benchmark datasets
- Proposing reference standards for other tissue systems
- Reviewing the lung benchmark methodology
- Improving documentation and tutorials
- Improving figure and report interpretation
- Testing reproducibility across operating systems
- Extending the framework to other biological systems
- Improving validation checks and metadata templates
- Contributing code for new benchmark modules

## Community questions

We invite discussion around these questions:

1. What should count as an appropriate reference standard for a specific model system?
2. Which public datasets should be included or excluded from a benchmark database?
3. What metadata are required to make benchmarking fair and interpretable?
4. Which metrics best capture biological fidelity?
5. How should results be reported so users understand both strengths and limitations?
6. Which tissue or model system should be extended next?

## Project status

This repository is being launched as the first open PhysioVerse project for community input, method review, and collaborative development.

## Repository structure

```text
docs/                         Methodology and contribution documentation
examples/lung-fidelity-demo/  Demo files and expected outputs
software/lung-fidelity-benchmark/  Software implementation area
.github/ISSUE_TEMPLATE/       Issue templates for community input
```


## Contact

For questions about the PhysioVerse ecosystem, open a GitHub Discussion or contact the project maintainers through the PhysioVerse website.
