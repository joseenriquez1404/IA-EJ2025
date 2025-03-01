# Line Charts
## Se cargan los datos
```python
spotify_filepath = "../input/spotify.csv"
spotify_data = pd.read_csv(spotify_filepath, index_col="Date", parse_dates=True)
```

## Graficar los datos
```python
#Agregar un titulo
plt.title("Daily Global Streams of Popular Songs in 2017-2018")

sns.lineplot(data=spotify_data)
```

## Graficar un subset de los datos
```python
plt.figure(figsize = (14,6))

# Add title
plt.title("Daily Global Streams of Popular Songs in 2017-2018")

# Line chart showing daily global streams of 'Shape of You'
sns.lineplot(data=spotify_data['Shape of You'], label="Shape of You")

# Line chart showing daily global streams of 'Despacito'
sns.lineplot(data=spotify_data['Despacito'], label="Despacito")

# Add label for horizontal axis
plt.xlabel("Date")
```