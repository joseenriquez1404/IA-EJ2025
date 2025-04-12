# Coordinate Reference Systems

Debido a que la tierra es 3D las proyecciones de 2D no son 100% precisas y se usa una tecnica llamada **map projection**

Existen varios **map projections** para diferentes situaciones como:

- Equal-area projections: Es útil para calcular el área de un pais, ciudad, etc.
- Equidistant projections: Sirve para calcular las distancias de vuelo.

Se usa un **coordinate reference system (CRS)** para mostrar como los puntos proyectados corresponden a lugares reales en la Tierra.

Cuando se crea el GeoDataFrame de un shapefile el CRS ya esta importado

```python
regions = gpd.read_file("../input/geospatial-learn-course-data/ghana/ghana/Regions/Map_of_Regions_in_Ghana.shp")
```

Si se crea un GeoDataFrame de un archivo CSV si es necesario hacer el CRS, con EPSG 4326 que corresponde a las coordenadas en latitud y longitud

```python
# Create a DataFrame with health facilities in Ghana
facilities_df = pd.read_csv("../input/geospatial-learn-course-data/ghana/ghana/health_facilities.csv")

# Convert the DataFrame to a GeoDataFrame
facilities = gpd.GeoDataFrame(facilities_df, geometry=gpd.points_from_xy(facilities_df.Longitude, facilities_df.Latitude))

# Set the coordinate reference system (CRS) to EPSG 4326
facilities.crs = {'init': 'epsg:4326'}

# View the first five rows of the GeoDataFrame
facilities.head()
```

Cuando se grafican diferentes GeoDataFrames es necesario que todos usen el mismo CRS.
```python
ax = regions.plot(figsize=(8,8), color='whitesmoke', linestyle=':', edgecolor='black')
facilities.to_crs(epsg=32630).plot(markersize=1, ax=ax)

# facilities.to_crs solo modifica la columna geometry
```

En caso de que el codigo EPSG no este disponible en GeoPandas se puede cambiar a "proj4 string"

```python
regions.to_crs("+proj=longlat +ellps=WGS84 +datum=WGS84 +no_defs").head()
```