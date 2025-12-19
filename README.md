# Kobe Bryant Shot Outcome Classification

This repository contains the code and analysis for a machine learning project investigating whether Kobe Bryant’s shot attempts can be accurately classified as made or missed using spatial, temporal, and shot-type information.

The project compares classical statistical methods with modern machine learning models, with a particular focus on interpretability and model performance.

---

## Research Question

> Can Kobe Bryant’s shot attempts be accurately classified as made or missed using spatial, temporal, and shot-type information?

---

## Data

- Kobe Bryant Dataset is based on his entire 20 year NBA career from 1996-2016
- The original dataset downloaded from Kaggle contains **30,697 observations and 25 variables**
- Shot attempts with missing shot outcomes (`shot_made_flag = NA`) were removed prior to modelling, as these observations cannot be used for supervised classification
- Several redundant or non-informative variables from the raw Kaggle dataset were removed during preprocessing
- All plots provided in this repository were generated using R

---

## Contents

- 5-slide presentation (excluding cover slide)
- 10-page written report (excluding cover page and table of contents)
- All models produced by R
- Kobe Bryant Dataset from Kaggle
---

## Author

**Danny Gomes**  



---

## Methodology

- Stratified 70/30 train–test split
- 5-fold cross-validation on training data
- Continuous predictors standardised using training data only

---

## Models Implemented

- Logistic Regression (classical baseline)
- Random Forest
- Support Vector Machine (Radial Kernel)
- Deep Learning (H2O)

---

## Model Interpretation

- Logistic regression coefficients and odds ratios were examined to assess effect size and direction
- Variable importance from tree-based models was used to identify dominant predictors

---

## Evaluation

- Model performance is primarily assessed using AUC (ROC)
- Accuracy, sensitivity, and specificity are reported for interpretability
- AUC was chosen due to class imbalance and threshold dependence of accuracy

---

## Key Results

| Model | AUC |
|------|-----|
| Logistic Regression | ~0.62 |
| Random Forest | ~0.61 |
| SVM (Radial) | ~0.61 |
| Deep Learning (H2O) | ~0.62 |

**Main findings:**
- All models achieved moderate discrimination
- Deep learning and other flexible models did not outperform logistic regression
- Variable importance analysis shows shot difficulty and location dominate prediction
- Performance is limited by missing contextual information (e.g. defender proximity)

  ## Limitations

- Defensive pressure and player-tracking data are not available
- Shot success contains inherent randomness beyond observable features
- Results should be interpreted as conditional on the available shot-level information


  ## How to Run the Code
  
 Install and load the required packages:

```r
library(tidyverse)
library(caret)
library(e1071)
library(randomForest)
library(pROC)
library(h2o)
library(cowplot)
```
Notes

- Random seeds are set to ensure reproducible results
  
- All models were trained and evaluated using the same train–test split
  
- Deep learning model was fitted using the H2O framework

- Model performance is reported on a held-out test set

- The focus of the project is model understanding, not maximising predictive accuracy
