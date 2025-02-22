# Categorical variables

Una **variable categorica** toma solo una cantidad limitada de valores numericos. Por ejemplo si haces una encuesta sobre que carros tienen las personas, las respuestas serían Honda, Nissan, etc.

Si tratas de ingresar estas variables a un modelo de ML va a generar errores por lo que es necesario procesarlas.

## Drop categorical variables
El método más fácil para lidiar con estas variables es eliminarlas.

```python
drop_X_train = X_train.select_dtypes(exclude=['object'])
drop_X_valid = X_valid.select_dtypes(exclude=['object'])
```

## Ordinal Encoding
Asigna un valor unico a un entero diferente

```python
from sklearn.preprocessing import OrdinalEncoder

label_X_train = X_train.copy()
label_X_valid = X_valid.copy()

ordinal_encoder = OrdinalEncoder()
label_X_train[object_cols] = ordinal_encoder.fit_transform(X_train[object_cols])

label_X_valid[object_cols] = ordinal_encoder.transform(X_valid[object_cols])
```

## One-Hot Encoding
Crea nuevas columnas indicando la presencia o absencia de cada posible valor en los datos originales.

```python
from sklearn.preprocessing import OneHotEncoder

#Aplicamos el one-hot enconder a cada columna categorica
OH_encoder = OneHotEncoder(handle_unknown='ignore', spare=False)
OH_cols_train = pd.DataFrame(OH_encoder.fit_transform(X_train[object_cols]))
OH_cols_valid = pd.DataFrame(OH_encoder.transform(X_valid[object_cols]))

#One hot encoding quita indexes por lo que se tienen que volver a agregar
OH_cols_train.index = X_train.index
OH_cols_valid.index = X_valid.index

#Se eliminan las variables categoricas
nun_X_train = X_train.drop(object_cols, axis=1)
nun_X_valid = X_valid.drop(object_cols, axis=1)

# Add one-hot encoded columns to numerical features
OH_X_train = pd.concat([num_X_train, OH_cols_train], axis=1)
OH_X_valid = pd.concat([num_X_valid, OH_cols_valid], axis=1)

# Ensure all columns have string type
OH_X_train.columns = OH_X_train.columns.astype(str)
OH_X_valid.columns = OH_X_valid.columns.astype(str)


```