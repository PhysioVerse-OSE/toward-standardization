# Interpretation Guide

## Spearman similarity

Higher Spearman correlation means the sample has gene-expression rank ordering more similar to the mean human reference profile.

## PCA centroid distance

Smaller PCA centroid distance means the model group is closer to the human reference centroid in the main PCA space.

## Dolan-Moré robustness profile

The Dolan-Moré profile shows how consistently each model stays close to the best-performing model across many PCA preprocessing choices.

## Combined interpretation

The strongest evidence of model fidelity comes from agreement across:

- high Spearman similarity
- low PCA centroid distance
- strong Dolan-Moré robustness
- low within-group dispersion

Results should be interpreted as benchmark proximity, not proof that a model fully reproduces human biology.
