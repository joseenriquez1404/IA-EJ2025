# Creating, reading and writing

Primero se debe de importar la libreria
```python
import panda as pd
```

### Creating data

Un **Dataframe** es una tabla que contiene entradas individuales, que cada una tiene un valor, cada una corresponde a una fila y columna

Por ejemplo:
```python
pd.Dataframe({'Yes': [50, 21], 'No': [131, 2]})
```
| | Yes| No |
| :---: | :---: | :---: |
| 0| 50| 131|
| 1| 21| 2|

Puede haber DataFrames donde los valores son strings.

```python
pd.DataFrame({'Bob': ['I liked it.', 'It was awful.'], 'Sue': ['Pretty good.', 'Bland.']})
```

| | Bob| Sue |
| :---: | :---: | :---: |
| 0|I liked it.|Pretty good|
| 1|It was awful.|Bland.|

```python
pd.DataFrame({'Bob': ['I liked it.', 'It was awful.'], 
              'Sue': ['Pretty good.', 'Bland.']},
             index=['Product A', 'Product B'])
```

## Series
Una **serie** es una lista y se puede crear a partir de una lista.
```python
pd.Series([1, 2, 3, 4, 5])
```
| | |
| :---: | :---: |
| 0|1|
| 1|2|
| 2|3|
| 3|4|
| 4|5|

```python
pd.Series([30, 35, 40], index=['2015 Sales', '2016 Sales', '2017 Sales'], name='Product A')
```

## Reading data files
Para leer desde un archivo CSV

```python
wine_reviews = pd.read_csv("../input/wine-reviews/winemag-data-130k-v2.csv")
```

Para saber que tan grande es el DataFrame
```python
wine_reviews.shape
```

Para ver las primeras cinco columnas

```python
wine_reviews.head()
```

Para guardar un DataFrame a un CSV 
```python
animals = pd.DataFrame({'Cows': [12, 20], 'Goats': [22, 19]}, index=['Year 1', 'Year 2']) #DataFrame

animals.csv("cows_and_goats.csv") #Aqui se gurda en el csv
```