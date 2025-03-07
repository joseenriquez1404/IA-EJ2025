# What is feature engineering

## Example
```python
import pandas as pd
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import cross_val_score

df = pd.read_csv("../input/fe-course-data/concrete.csv")
```

```python
X = df.copy()
y = X.pop("CompressiveStrength")

# Entrenar y evaluar el modelo
baseline = RandomForestRegressor(criterion = "absolute_error", random_state = 0)
baseline_score = cross_val_score(
    baseline, X, y, cv = 5, scoring = "neg_mean_absolute_error"
)
baseline_score = -1 * baseline_score.mean()
```

```python
X = df.copy()
y = X.pop("CompressiveStrength")

# Crear funciones sinteticas
X["FCRatio"] = X["FineAggregate"] / X["CoarseAggregate"]
X["AggCmtRatio"] = (X["CoarseAggregate"] + X["FineAggregate"]) / X["Cement"]
X["WtrCmtRatio"] = X["Water"] / X["Cement"]

# Train and score model on dataset with additional ratio features
model = RandomForestRegressor(criterion="absolute_error", random_state=0)
score = cross_val_score(
    model, X, y, cv=5, scoring="neg_mean_absolute_error"
)
score = -1 * score.mean()
```