# Manipulating Geospatial Data

## Geocoding
Es el proceso de convertir el nombre de un lugar o la dirección a una ubicación en el mapa.

Para esto se ocupa la siguiente libreria
```python
from geopy.geocoders import Nominatim
```

`Nominatim` Es el software de geocoding que se usara para generar las ubicaciones.

```python
geolocator = Nominatim(user_agent="kaggle_learn")
location = geolocator.geocode("Pyramid of Khufu")

print(location.point) # 29 58m 44.976s N, 31 8m 3.17625s E
print(location.address) # هرم خوفو, شارع ابو الهول السياحي, نزلة البطران, الجيزة, 12125, مصر
```

```python
point = location.point 
print("Latitude:", point.latitude) # 29.97916
print("Longitude:", point.longitude) # 31.134215625236113
```

Un ejemplo de su uso es que si queremos obtener las ubicaciones de diferentes universidades de Europa
```python
universities = pd.read_csv("../input/geospatial-learn-course-data/top_universities.csv")
universities.head()
```

```python
def my_geocoder(row):
    try:
        point = geolocator.geocode(row).point
        return pd.Series({'Latitude': point.latitude, 'Longitude': point.longitude})
    except:
        return None

universities[['Latitude', 'Longitude']] = universities.apply(lambda x: my_geocoder(x['Name']), axis=1)

print("{}% of addresses were geocoded!".format(
    (1 - sum(np.isnan(universities["Latitude"])) / len(universities)) * 100))

# Drop universities that were not successfully geocoded
universities = universities.loc[~np.isnan(universities["Latitude"])]
universities = gpd.GeoDataFrame(
    universities, geometry=gpd.points_from_xy(universities.Longitude, universities.Latitude))
universities.crs = {'init': 'epsg:4326'}
universities.head()
```

Luego creamos un mapa para visualizar las ubicaciones
```python
# Create a map
m = folium.Map(location=[54, 15], tiles='openstreetmap', zoom_start=2)

# Add points to the map
for idx, row in universities.iterrows():
    Marker([row['Latitude'], row['Longitude']], popup=row['Name']).add_to(m)

# Display the map
m
```