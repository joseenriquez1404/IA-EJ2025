# Cross Validation

En **cross validation** se corre nuestro modelo a traves de diferentes subsets de datos para obtener multiples medidas de calidad del modelo.
Se utiliza en datasets pequeños ya que utiliza muchos recursos, además es más fácil realizarlo con **Pipelines** 

```python
from sklearn.ensemble import RandomForestRegressor
from sklearn.pipeline import Pipeline
from sklearn.impute import SimpleImputer

my_pipeline = Pipeline(steps = [('preprocessor', SimpleImputer()), ('model', RandomForestRegressor(n_estimators = 50, random_state = 0))])
```

Luego se obtienen las puntuaciones
```python
from sklearn.model_selection import cross_val_score

# Se multiplica por -1 ya que sklearn calcula -MAE
scores = -1 * cross_val_score(my_pipeline, X, y, cv = 5, scoring = 'neg_mean_absolute_error)

#Cv son la cantidad de subsets
```