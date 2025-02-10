# Grouping and Sorting

## Groupwise analysis
Podemos replicar la función *value_counts()* con la función *groupby()*, por ejemplo: 
```python
reviews.groupby('points').points.count()
```

También si queremos encontrar el precio más bajo lo podemos hacer de la siguiente manera:
```python
reviews.groupby('points').price.min()
```

Si queremos manipular los datos podemos usar el método *apply()*, por ejemplo si queremos tomar el primer nombre de cada casa de vinos:
```python
reviews.groupby('winery').apply(lambda df: df.title.iloc[0])
```

Otro ejemplo más complejo es obtener el mejor vino de cada país y de cada provincia.
```python
reviews.groupby(['country', 'province']).apply(lambda df: df.loc[df.points.idxmax()])
```

Otro método de *groupby()* es *agg()* que nos permite realizar diferentes funciones en nuestro DataFrame
```python
reviews.groupby(['country']).price.agg([len, min, max])
#Esto genera una tabla con los paises como filas y con tres columnas las cuales son len, min y max
```

## Multi-indexes
Para convertir de un multi-index a un index regular se hace de la siguiente manera:
```python
countries_reviewed = reviews.groupby(['country', 'province']).description.agg([len])

countries_reviewed.reset_index()
```

## Sorting
El código anterior nos devuelve una tabla pero la columna "len" no esta ordenada de menor a mayor esto se puede hacer de la siguiente manera:
```python
countries_reviewed = countries_reviewed.reset_index()
countries_reviewed.sort_values(by = 'len') #Ascendente
countries_reviewed.sort_values(by = 'len', ascending = False) #Descendiente
```

Si queremos ordenar los indices
```python
countries_reviewed.sort_index()
```

También se pueden ordenar varias columnas a la vez
```python
countries_reviewed.sort_values(by = ['country', 'len'])
```