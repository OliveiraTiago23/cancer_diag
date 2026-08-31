Breast Cancer Diagnosis with Machine Learning
Overview
This project explores the use of machine learning for breast cancer classification.

The objective is to build a model capable of classifying tumors as benign or malignant based on numerical characteristics extracted from cell nuclei.

The project uses a Decision Tree Classifier and focuses on understanding how model performance can be improved through hyperparameter optimization.

Important: This project is intended for educational and research purposes only. It is not a medical diagnostic tool and should not be used to make clinical decisions.

Dataset
The dataset contains 569 observations and 20 numerical features describing characteristics of cell nuclei, together with a binary target variable.

The features include measurements such as:

Mean radius
Mean texture
Mean perimeter
Mean area
Mean smoothness
Mean compactness
Mean concavity
Mean concave points
Mean symmetry
Mean fractal dimension
Worst radius
Worst texture
Worst perimeter
Worst area
Worst smoothness
Worst compactness
Worst concavity
Worst concave points
Worst symmetry
Worst fractal dimension
The target variable represents the tumor classification:

0 → Benign
1 → Malignant
Project Workflow
The notebook follows a complete machine learning workflow.

1. Data exploration
The dataset is loaded with Pandas and explored to understand its structure, variables, and distributions.

Histograms are used to visualize the distribution of the different features.

2. Feature and target separation
The dataset is divided into:

X: the explanatory variables/features
y: the target variable
The target column is removed from X and kept separately in y.

3. Train, validation and test sets
The dataset is divided into three subsets:

Training set: 343 observations
Validation set: 113 observations
Test set: 113 observations
The training set is used to train the models, the validation set is used to compare different model configurations, and the test set is reserved for the final evaluation.

4. Initial Decision Tree
A DecisionTreeClassifier is first trained using the training data.

The model's performance is evaluated using a confusion matrix and several classification metrics.

5. Model evaluation
Three main metrics are used to evaluate the classifier:

Accuracy – the overall proportion of correctly classified observations.
Recall (Sensitivity) – the proportion of malignant tumors correctly identified.
Specificity – the proportion of benign tumors correctly identified.
The F1 score is also used to evaluate the balance between precision and recall.

6. Manual hyperparameter optimization
The model is optimized by testing different values for:

max_leaf_nodes
max_depth
Different decision trees are trained and evaluated on the validation set.

This makes it possible to identify configurations that reduce the misclassification rate.

7. GridSearchCV
Instead of manually testing only a few parameters, GridSearchCV is then used to systematically explore multiple combinations of hyperparameters.

The search considers parameters such as:

criterion
max_depth
max_features
max_leaf_nodes
min_samples_leaf
min_samples_split
The best combination is selected according to accuracy.

8. Final model
The best model found by GridSearchCV is then evaluated on the test set, which was not used during the hyperparameter search.

The best configuration found in the notebook is:

criterion = gini
max_depth = 7
max_features = sqrt
max_leaf_nodes = 14
min_samples_leaf = 1
min_samples_split = 2

Results
The final model achieved the following results on the test set:

Metric	Score
Accuracy	97.35%
Recall	97.44%
Specificity	97.30%
F1 Score	0.9620
Misclassification rate	2.65%

These results indicate that the optimized decision tree performs well on the test dataset, correctly identifying a high proportion of both malignant and benign tumors.

Technologies Used
Python
Pandas – data manipulation
NumPy – numerical operations
Matplotlib – data visualization
Seaborn – data visualization
Scikit-learn – machine learning and model evaluation
Jupyter Notebook – development environment
