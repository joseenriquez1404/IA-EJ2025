# Summary Functions and Maps
## Summay functions
La función *describe()* estructura la información de una forma funcional.
Por ejemplo:
```python
reviews.points.describe()
```
Esto nos regresa la siguiente tabla:
| count | 129971.00000 |
|-------|--------------|
| mean  | 88.447138    |
|       | ...          |
| 75%   | 91.00000     |
| max   | 100.00000    |

También se puede obtener la media de una columna:
```python
reviews.points.mean()
```
Para ver una lista con todos los elementos unicos de la columna
```python
reviews.taster_name.unique()
```
Para ver una lista con valores unicos y cuantas veces aparecen en el dataset.
```python
reviews.taster_name.value_counts()
```

## Maps
Un **mapa** es una función que toma un set de valores y los *mapea* a otro set de valores.

Uno de los métodos para mapear es el siguiente de la
```python
review_points_mean = review.points.mean()
revies.points.map(lambda p: p - reviews_points_mean)
```

La función *map* espera un solo valor de la **Serie** y regresa una versión transformada del mismo.

El método *apply()* es el equivalente si queremos transformar todo un DataFrame llamando un método especial para cada fila.

```python
def remean_points(row):
    row.points = row.points - review_points_mean
    return row

reviews.apply(remean_points, axis = 'columns')
```