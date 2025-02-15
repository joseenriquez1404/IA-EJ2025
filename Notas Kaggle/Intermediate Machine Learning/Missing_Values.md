# Missing Values
## Eliminar columnas con "missing values"
Puedes eliminar columnas con muchos valores perdidos pero los que si estan puesden ser valores muy utiles.

```python
#Obtener las columnas con valores vacios
cols_with_missing = [col for col in X_train.columns if X_train[col].isnull().any()]

#Eliminar las columnas en el entrenamiento y validacion
reduced_X_train = X_train.drop(cols_with_missing, axis=1)
reduced_X_valid = X_valid.drop(cols_with_missing, axis=1)
```

## Imputation
Aquí es asignarle un valor al espacio vacio, esto puede ser la media de la columna.

```python
from sklearn.impute import SimpleImputer

my_imputer = SimpleImputer()
imputed_X_train = pd.DataFrame(my_imputer.fit_transform(X_train))
imputed_X_valid = pd.DataFrame(my_imputer.transform(X_valid))

imputed_X_train.columns = X_train.columns
imputed_X_valid.columns = X_valid.columns

```

## Extensión de imputation
En este se hace lo mismo de que **imputation** pero además se crea una nueva columna donde se especifica donde estan valores faltantes.

```python
X_train_plus = X_train.copy()
X_valid_plus = X_valid.copy()

for col in cols_with_missing:
    X_train_plus[col + '_was_missing'] = X_train_plus[col].isnull()
    X_valid_plus[col + '_was_missing'] = X_valid_plus[col].isnull()

my_imputer = SimpleImputer()
imputed_X_train_plus = pd.DataFrame(my_imputer.fit_transform(X_train_plus))
imputed_X_valid_plus = pd.DataFrame(my_imputer.transform(X_valid_plus))

imputed_X_train_plus.columns = X_train_plus.columns
imputed_X_valid_plus.columns = X_valid_plus.columns
```