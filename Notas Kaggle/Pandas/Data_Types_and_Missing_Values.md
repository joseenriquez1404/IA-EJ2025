# Data Types and Missing Values

## Dtypes
El tipo de dato de un DataFrame es **dtype**
Para saber el tipo de dato de una columna de un DataFrame se puede hacer de la siguiente manera:
```python
reviews.price.dtype #Regresa el tipo de dato de una columna de una columna
reviews.dtype #Regresa el tipo de dato de todas las columnas.
```

Para cambiar el tipo de dato se puede hacer de la siguiente manera:
```python
reviews.points.astype('float64') #Convierte de int64 a float64
```

## Missing Data
Los valores perdidos se representan como **NaN**.

Para encontrar los valores **NaN** se pueden encontrar de la siguiente manera:
```python
reviews[pd.isnull(reviews.country)]
```

Para poder cambiar **NaN** por otra cosa se puede hacer de la siguiente manera:
```python
reviews.region_2.fillna("Unknown")
```

Si queremos cambiar un valor que no es **NaN** se puede hacer de la siguiente manera:
```python
reviews.taster_twitter_handle.replace("@Kerinokeefe", "@kerino")
```