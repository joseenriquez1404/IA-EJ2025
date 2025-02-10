# Indexing, selecting and assigning

## Native accesors
Si tenemos el siguiente DataFrame **reviews**, podemos acceder a una propiedad de la siguiente forma
```python
reviews.country
```
Si tuvieramos un diccionario pudieramos acceder a sus valores mediante el operador []
```python
reviews['country']
```
Las dos formas anteriores no regresan los mismos valores y lo que nos regresa es una **Serie**.

Si solo queremos acceder a un valor en especifico podemos hacer lo siguiente
```python
reviews['country'][0]
```

## Indexing in Pandas
Pandas tiene sus propios operadores de accesamiento como *loc* y *iloc*, estos sirven para operaciones más avanzadas.

### Index-based selection
El **index-based selection** selecciona los datos basados en su posición numerica. *Iloc* es el que sigue este paradigma.

Para seleccionar la primera fila del DataFrame se hace de la siguiente manera:
```python
reviews.iloc[0]
```

Tanto *loc* y *Iloc* son primero fila y luego columna.

Para obtener una columna con *iloc* se hace de la siguiente manera:
```python
reviews.iloc[:, 0]
```

Si lo queremos las primeras 3 filas de la primera columna
```python
reviews.iloc[:3, 0]
```

Si solo queremos la primera y segunda entrada

```python
reviews.iloc[1:3, 0]
```

También es posible pasar una lista.
```python
reviews.iloc[[0, 1, 2], 0]
```

También es posible pasar numeros negativos los cuales nos regresa los ultimos valores del DataFrame
```python
reviews.iloc[-5:]
```

### Label-based selection
Aquí se utiliza el operador *loc* aquí nos interesesa el index del valor de los datos.
Para acceder a un valor se hace de la siguiente manera.
```python
reviews.loc[0, 'country']
```

Cuando usamos *iloc* tratamos al dataset como una matriz grande, mientras que *loc* usa la información en los indices para hacer el trabajo.

Un ejemplo de una operación que se hace más sencilla usando *loc* es:
```python
reviews.loc[:, ['taste_name', 'taster_twitter_handle', 'points']]
```

### Manipulating the index
El método **set_index()** sirve para manipular el index de la forma más conveniente que veamos.
```python
reviews.set_index("title") # Crea una nueva fila con el nombre de "title"
```
### Conditional selection
Un ejemplo para este caso, es saber los mejores vinos de italia. Primero podemos checar si el vino es de Italia de la siguiente manera:
```python
reviews.country == 'Italy' #Se genera una lista de True o False en cada país de los datos
```

También podemos encontrar la información con un *loc*
```python
reviews.loc[reviews.country == 'Italy']
```

Tambien como queremos los mejores hay que agregar otra condición para la calificación del vino
```python
reviews.loc[(reviews.country == 'Italy') & (reviews.points >= 90)]
```

Si queremos comprar un vino que sea Italiano o mejor que el promedio
```python
reviews.loc[(reviews.country == 'Italy') | (reviews.points >= 90)]
```

Pandas también viene con la funcion *isin* el cual nos permite seleccionar aquellos valores dentro de una lista de valores de
```python
reviews.loc[reviews.country.isin(['Italy', 'France')]]
```

También existe *isnull* y *notnull* los cuales seleccionan aquellos que estan vacios y aquellos que no.
```python
reviews.loc[reviews.price.notnull()]
```

### Asigning data
También se puede asignar valores a un DataFrame
```python
reviews['critic'] = 'everyone'
```

```python
reviews['critic'] = range(len(reviews), 0, -1)
```