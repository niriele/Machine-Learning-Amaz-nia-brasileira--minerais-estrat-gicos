# Influences of Sampling Design and Model Selection on Predictions of Chemical Compounds in Petroferric Formations in the Brazilian Amazon

This repository contains the R workflow associated with the peer-reviewed article published in *Remote Sensing* (2025), volume 17, issue 9, article 1644.

> Rodrigues, N. B., Barbosa, T. R. P., Pinheiro, H. S. K., Mancini, M., Read, Q. D., Blackstock, J., Winzeler, H. E., Miller, D., Owens, P. R., & Libohova, Z. (2025). Influences of Sampling Design and Model Selection on Predictions of Chemical Compounds in Petroferric Formations in the Brazilian Amazon. *Remote Sensing, 17*(9), 1644. https://doi.org/10.3390/rs17091644

## Overview

Morro dos Seis Lagos, in the Brazilian Amazon, contains a rare petroferric/lateritic formation associated with one of the world's largest known niobium reserves. This study evaluates how sampling design and machine-learning model selection affect spatial predictions of six major chemical compounds:

- Al₂O₃ (aluminum oxide)
- Fe₂O₃ (iron oxide)
- MnO (manganese oxide)
- Nb₂O₅ (niobium oxide)
- TiO₂ (titanium dioxide)
- SiO₂ (silicon dioxide)

## Objectives

The study evaluates the performance of five machine-learning models across five sampling scenarios derived from three sampling designs, including the interactions between sampling strategy, model choice, and prediction accuracy.

The following alternative hypotheses were tested:

1. Predictions of different chemical elements are influenced by sampling design.
2. The performance of all models depends on sampling design.
3. Model performance differs among chemical elements.
4. Predictions are influenced by the interaction between sampling design and model choice.

## Machine-learning models

The workflow implements five regression algorithms through the `caret` ecosystem:

- Generalized Linear Models with Elastic Net Regularization (`glmnet`)
- Random Forest (`rf`)
- Neural Network (`nnet`)
- Support Vector Machine with radial kernel (`svmRadial`)
- k-Nearest Neighbors (`knn`)

Recursive Feature Elimination (RFE) is used for covariate selection. Model assessment includes RMSE, MAE, R², bias, and correlation-based agreement metrics.

## Repository structure

```text
.
├── README.md
├── CITATION.cff
├── .gitignore
├── scripts/
│   └── loop_nnet_rf_svm_knn_mlp.R
├── data/
│   └── README.md
└── raster/
    └── README.md
```

## Input data

The script expects the following local inputs:

```text
data/training.csv
data/validation.csv
raster/*.tif
```

The analytical data and raster covariates are not included in this initial public release. Users must provide files with the same structure and variable names expected by the script.

## R dependencies

The main packages used are:

```r
readr, dplyr, doParallel, caret, terra, sf, sp, tibble,
ggplot2, forcats, corrplot, ggcorrplot, RSNNS, randomForest,
kernlab, nnet, glmnet, Matrix, stringr
```

## Running the workflow

1. Clone or download this repository.
2. Place the tabular input files in `data/`.
3. Place the raster covariates in `raster/`.
4. Open R in the repository root.
5. Run `scripts/loop_nnet_rf_svm_knn_mlp.R`.

The workflow can be computationally intensive because it performs repeated feature selection, cross-validation, model fitting, validation, and raster prediction.

## Article

- [Full article](https://www.mdpi.com/2072-4292/17/9/1644)
- [DOI: 10.3390/rs17091644](https://doi.org/10.3390/rs17091644)

## Authors

Niriele B. Rodrigues, Theresa R. P. Barbosa, Helena S. K. Pinheiro, Marcelo Mancini, Quentin D. Read, Joshua Blackstock, Hans E. Winzeler, David Miller, Phillip R. Owens, and Zamir Libohova.

## Reuse and citation

If this workflow contributes to your research, please cite the published article using the citation above. No software license has been assigned in this initial release; reuse of the source code therefore requires permission from the copyright holder(s).
