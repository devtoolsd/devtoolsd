---
name: scikit-learn
slug: scikit-learn
language: python
description: The standard Python machine learning library — consistent API for classification, regression, clustering, and preprocessing.
logo: https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg
website: https://scikit-learn.org
github: scikit-learn/scikit-learn
year: 2007
pricing: free
open_source: true
license: BSD-3-Clause
tool_type: data
tags: [ml, data-science, classification, regression, clustering, python, preprocessing]
related_frameworks: [pytorch, tensorflow, pandas]
features:
  - "Consistent `fit / transform / predict` API across all algorithms"
  - "Classification: SVM, Random Forest, Gradient Boosting, KNN, Logistic Regression"
  - "Regression: Ridge, Lasso, ElasticNet, Random Forest, XGBoost integration"
  - "Clustering: K-Means, DBSCAN, hierarchical, spectral"
  - "Preprocessing: StandardScaler, MinMaxScaler, LabelEncoder, OneHotEncoder"
  - "Pipeline API for combining preprocessing and model steps"
  - "GridSearchCV and RandomizedSearchCV for hyperparameter tuning"
  - "Cross-validation, learning curves, and model evaluation metrics"
install:
  pip: "pip install scikit-learn"
  conda: "conda install scikit-learn"
---

Scikit-learn provides a consistent `fit/transform/predict` API across dozens of classical ML algorithms — SVMs, decision trees, random forests, gradient boosting, k-means, and more. It integrates seamlessly with NumPy and Pandas and is the starting point for most data science ML workflows before graduating to deep learning. Its Pipeline API chains preprocessing and modeling into reproducible, cross-validation-friendly workflows.

## Quick start

```bash
pip install scikit-learn pandas numpy
```

```python
import numpy as np
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestClassifier
from sklearn.pipeline import Pipeline
from sklearn.metrics import classification_report

# Load data
X, y = load_iris(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Build pipeline
pipe = Pipeline([
    ('scaler', StandardScaler()),
    ('clf', RandomForestClassifier(n_estimators=100, random_state=42)),
])

# Train and evaluate
pipe.fit(X_train, y_train)
y_pred = pipe.predict(X_test)
print(classification_report(y_test, y_pred, target_names=load_iris().target_names))

# Cross-validation
cv_scores = cross_val_score(pipe, X, y, cv=5)
print(f"CV accuracy: {cv_scores.mean():.3f} ± {cv_scores.std():.3f}")
```

```python
# Hyperparameter tuning
from sklearn.model_selection import GridSearchCV

param_grid = {
    'clf__n_estimators': [50, 100, 200],
    'clf__max_depth': [None, 5, 10],
}

search = GridSearchCV(pipe, param_grid, cv=5, n_jobs=-1)
search.fit(X_train, y_train)
print("Best params:", search.best_params_)
```

## When to use

scikit-learn is the first stop for any Python ML project using classical algorithms — tabular data, feature engineering, and model evaluation. Its Pipeline API is excellent for production code that needs reproducible preprocessing. For deep learning and neural networks, PyTorch or TensorFlow/Keras are required. For large tabular datasets, XGBoost and LightGBM complement scikit-learn's API and often outperform its gradient boosting implementation.
