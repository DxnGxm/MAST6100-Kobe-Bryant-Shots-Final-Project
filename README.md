# Kobe Bryant Shot Outcome Classification

This repository contains the code and analysis for a machine learning project investigating whether Kobe Bryant’s shot attempts can be accurately classified as made or missed using spatial, temporal, and shot-type information.

The project compares classical statistical methods with modern machine learning models, with a particular focus on interpretability and model performance.

---

## Research Question

> Can Kobe Bryant’s shot attempts be accurately classified as made or missed using spatial, temporal, and shot-type information?

---

## Data

- Shot-level NBA data covering Kobe Bryant’s career  
- Binary response variable: `shot_made_flag` (Made / Miss)  

**Key predictors include:**
- Spatial location (`loc_x`, `loc_y`, `shot_zone_basic`)
- Temporal context (`minutes_remaining`, `seconds_remaining`, `period`)
- Shot characteristics (`shot_distance`, `shot_type`, `combined_shot_type`)
- Game context (`playoffs`, `clutch`)

Missing shot outcomes were removed prior to modelling.

---

## Methodology

- Stratified 70/30 train–test split
- 5-fold cross-validation on training data
- Continuous predictors standardised using training data only
- Models evaluated using ROC curves and AUC, rather than accuracy alone, due to class imbalance

---

## Models Implemented

- Logistic Regression (classical baseline)
- Random Forest
- Support Vector Machine (Radial Kernel)
- Deep Learning (H2O)

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

-Results are reproducible using the provided random seeds

-Model performance is reported on a held-out test set

-The focus of the project is model understanding, not maximising predictive accuracy
