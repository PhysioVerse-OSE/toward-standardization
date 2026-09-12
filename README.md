<div align="center">

<a href="https://physioverse.org/">
  <img src="https://physioverse.org/branding/physioverse-logo.png" alt="PhysioVerse" width="620" />
</a>

# Toward Standardization

### Reference-anchored benchmarking for advanced in vitro biological models

A PhysioVerse open-source project for transparent and reproducible evaluation of how closely an in vitro model reflects an appropriate biological reference.

<a href="https://physioverse.org/tools"><strong>PhysioVerse Tools</strong></a>
&nbsp;&nbsp;•&nbsp;&nbsp;
<a href="https://physioverse.org/"><strong>PhysioVerse.org</strong></a>
&nbsp;&nbsp;•&nbsp;&nbsp;
<a href="https://github.com/PhysioVerse-OSE"><strong>PhysioVerse GitHub</strong></a>

</div>

---

## Overview

Toward Standardization provides reproducible workflows for evaluating biological fidelity across advanced in vitro model systems.

The first implementation is a **lung epithelial culture fidelity benchmark** that compares healthy, mock, untreated, or baseline lung epithelial culture RNA-seq profiles with a fixed healthy human distal lung tissue reference using interpretable transcriptomic metrics.

The reference serves as an anchor for measuring and reporting biological proximity while preserving the identity of each model system.

---

## Why This Project Matters

Organoids, body-on-chip systems, organ tissue equivalents, tissue chips, and other microphysiological systems are increasingly used to model human biology.

A recurring question is:

> How closely does an experimental model reflect the biological system it is intended to represent?

Toward Standardization provides a transparent framework for addressing that question through declared reference datasets, shared gene-space harmonization, interpretable metrics, robustness analysis, and reproducible reporting.

---

## Lung Fidelity Benchmark

The first benchmark asks:

> Which two-dimensional or three-dimensional lung epithelial culture system is transcriptomically closest to healthy human distal lung tissue?

The built-in benchmark includes:

- **GSE165192-Human** as the fixed healthy human distal lung tissue reference
- NHBE 2D primary monolayer samples
- A549 and A549-ACE2 2D immortalized monolayer samples
- Calu-3 epithelial monolayer samples
- hBEpC 2D primary monolayer samples
- hBO bronchial organoids
- ALI-HBEC differentiated epithelium
- OTE engineered airway organ tissue equivalents

Healthy, mock, untreated, or baseline samples are used to reduce confounding from infection, drug treatment, genetic perturbation, or disease-associated transcriptional responses.

---

## Core Metrics

<table>
<tr>
<td width="50%" valign="top">

### PCA Centroid Distance

Measures global transcriptomic proximity between each model group and the fixed human distal lung reference centroid.

</td>
<td width="50%" valign="top">

### Spearman Correlation

Measures sample-wise gene-expression rank similarity to the mean human distal lung reference profile.

</td>
</tr>
</table>

The workflow also evaluates robustness across PCA preprocessing choices, including a **Dolan-Moré performance profile**.

---

## Software Modes

| Mode | Purpose |
|---|---|
| **Demo** | Run the full benchmark using the built-in lung reference database. |
| **Simple user** | Add one expression CSV and compare a new model with the built-in database. |
| **Advanced user** | Analyze multiple user datasets or multiple culture-system groups with metadata. |

---

## Input Data

User-provided expression data should be supplied as CSV files. The first column must be named exactly:

```text
Gene Symbol
```

Each remaining column should represent one RNA-seq sample. Rows represent genes, and values should be raw or count-like non-negative expression values.

Example:

```csv
Gene Symbol,Sample_1,Sample_2,Sample_3
TP53,120,135,141
EPCAM,500,490,510
KRT8,850,870,860
```

Recommended inputs include human gene symbols, raw or count-like expression values, healthy/mock/untreated/baseline samples, biological replicates when available, and metadata describing culture system and technical batches.

Already z-scored or batch-corrected values should not be used as benchmark input.

For additional details, see [`docs/data-format.md`](docs/data-format.md).

---

## Documentation

| Resource | Description |
|---|---|
| [`docs/methodology.md`](docs/methodology.md) | Benchmark methodology and analysis approach |
| [`docs/reference-standard-selection.md`](docs/reference-standard-selection.md) | Guidance for selecting biological reference standards |
| [`docs/data-format.md`](docs/data-format.md) | Input structure and formatting guidance |
| [`docs/interpretation-guide.md`](docs/interpretation-guide.md) | Guidance for interpreting benchmark outputs |
| [`examples/lung-fidelity-demo/`](examples/lung-fidelity-demo/) | Lung fidelity demonstration resources |
| [`software/lung-fidelity-benchmark/`](software/lung-fidelity-benchmark/) | Software implementation area |

---

## Contribute

Contributions are welcome in areas such as additional public benchmark datasets, biological reference selection, methodology review, documentation, tutorials, reproducibility testing, metadata templates, validation checks, extensions to additional tissue systems, and new benchmark modules.

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for contribution guidance.

---

## PhysioVerse

Toward Standardization is part of the broader PhysioVerse ecosystem.

<p align="center">
  <a href="https://physioverse.org/"><strong>Visit PhysioVerse</strong></a>
  &nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="https://physioverse.org/tools"><strong>Explore Tools</strong></a>
  &nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="https://physioverse.org/community"><strong>Community</strong></a>
  &nbsp;&nbsp;•&nbsp;&nbsp;
  <a href="https://physioverse.org/contact"><strong>Contact</strong></a>
</p>


<!-- physioverse:task-update-v14:scientific-resource-contribution:start -->
## Contribute to This Resource

Share method feedback, report a reproducibility issue, or propose a focused documentation improvement. Include the relevant workflow, source, and expected or observed behavior.

**[Open an Issue](https://github.com/PhysioVerse-OSE/toward-standardization/issues/new/choose)** | **[View open work](https://github.com/PhysioVerse-OSE/toward-standardization/issues)** | **[Propose a document change](https://github.com/PhysioVerse-OSE/PhysioVerse-OSE/blob/main/START_CONTRIBUTING.md#two-ways-to-contribute)**
<!-- physioverse:task-update-v14:scientific-resource-contribution:end -->
