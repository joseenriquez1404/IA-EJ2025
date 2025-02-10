# Renaming and Combining
## Renaming
Para poder cambiar el nombre de los indices o de las columnas
```python
reviews.rename(columns = {'points': 'score'})
```

Para poder cambiar los indices:
```python
reviews.rename(0: 'firstEntry', 1: 'secondEntry')
```

Para renombrar los ejes:
```python
reviews.rename_axis("wines", axis = 'rows').rename_axis("fields", axis = 'columns')
```

## Combining
Es cuando tenemos que juntar dos DataFrames

### Concat
```python
canadian_youtube = pd.read_csv("../input/youtube-new/CAvideos.csv")
british_youtube = pd.read_csv("../input/youtube-new/GBvideos.csv")

pd.concat([canadian_youtube, british_youtube])
```

### Join
```python
left = canadian_youtube.set_index(['title', 'trending_date'])
right = british_youtube.set_index(['title', 'trending_date'])

left.join(right, lsuffix='_CAN', rsuffix='_UK')
```