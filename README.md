# Breast Cancer Diagnosis with Machine Learning

## Overview

This project explores the use of machine learning for breast cancer classification.

The objective is to build a model capable of classifying tumors as **benign or malignant** based on numerical characteristics extracted from cell nuclei.

The project uses a **Decision Tree Classifier** and focuses on improving model performance through hyperparameter optimization.

> **Important:** This project is intended for educational purposes only. It is not a medical diagnostic tool and should not be used to make clinical decisions.

## Dataset

The dataset contains **569 observations** and **20 numerical features** describing characteristics of cell nuclei, together with a binary target variable.

The features include:

- Mean radius
- Mean texture
- Mean perimeter
- Mean area
- Mean smoothness
- Mean compactness
- Mean concavity
- Mean concave points
- Mean symmetry
- Mean fractal dimension
- Worst radius
- Worst texture
- Worst perimeter
- Worst area
- Worst smoothness
- Worst compactness
- Worst concavity
- Worst concave points
- Worst symmetry
- Worst fractal dimension

The target variable represents the tumor classification:

- `0` → Benign
- `1` → Malignant

## Project Workflow

The notebook follows a complete supervised machine learning workflow.

### 1. Data Exploration

The dataset is loaded and explored using Pandas to understand its structure, variables, and distributions.

Histograms are used to visualize the distribution of the different features.

### 2. Feature and Target Separation

The dataset is divided into:

- `X`: the explanatory variables/features
- `y`: the target variable

The target column is removed from `X` and kept separately in `y`.

### 3. Train, Validation and Test Sets

The dataset is divided into three subsets:

- **Training set:** 343 observations
- **Validation set:** 113 observations
- **Test set:** 113 observations

The training set is used to train the models, the validation set is used to compare different model configurations, and the test set is reserved for the final evaluation.

### 4. Initial Decision Tree

A `DecisionTreeClassifier` is first trained using the training data.

The model's performance is evaluated using a confusion matrix and several classification metrics.

### 5. Model Evaluation

The model is evaluated using several metrics:

- **Accuracy** – the overall proportion of correctly classified observations.
- **Recall (Sensitivity)** – the proportion of malignant tumors correctly identified.
- **Specificity** – the proportion of benign tumors correctly identified.
- **F1 Score** – a metric combining precision and recall.

### 6. Manual Hyperparameter Optimization

The decision tree is optimized by testing different values for:

- `max_leaf_nodes`
- `max_depth`

Different decision trees are trained and evaluated on the validation set.

This allows us to identify configurations that reduce the misclassification rate.

### 7. GridSearchCV

To explore a larger number of possible hyperparameter combinations, `GridSearchCV` is used.

The search considers parameters such as:

- `criterion`
- `max_depth`
- `max_features`
- `max_leaf_nodes`
- `min_samples_leaf`
- `min_samples_split`

The best combination is selected according to accuracy.

### 8. Final Model

The best model found by `GridSearchCV` is then evaluated on the test set, which was not used during the hyperparameter optimization process.

The best configuration found in the notebook is:

```text
criterion = gini
max_depth = 7
max_features = sqrt
max_leaf_nodes = 14
min_samples_leaf = 1
min_samples_split = 2
