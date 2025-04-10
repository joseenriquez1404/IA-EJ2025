# Handling Missing Values

## Paso 1 
Importamos los datos y las librerias necesarias
```python
import pandas as pd
import numpy as np

# read in all our data
nfl_data = pd.read_csv("../input/nflplaybyplay2009to2016/NFL Play by Play 2009-2017 (v4).csv")

# set seed for reproducibility
np.random.seed(0) 
```

Luego se ve un poco de los datos para ver con que estamos trabajando
```python
nfl_data.head()
```

## Paso 2
Cuantos valores nulos tenemos por cada columna
```python
missing_values_count = nfl_data.isnull().sum()

missing_values_count[0:10]
```

Para eliminar todas las filas con valores nulos
```python
nfl_data.dropna()
```

Para eliminar todas las columnas que tienen valores nulos
```python
columns_with_na_dropped = nfl_data.dropna(axis=1)
columns_with_na_dropped.head()
```

Si queremos modificar los valores nulos por otro valor
```python
subset_nfl_data.fillna(0)
```

Para que un valor nulo tenga el siguiente valor o si no cero
```python
subset_nfl_data.fillna(method = "bfill", axis = 0).fillna(0)
```