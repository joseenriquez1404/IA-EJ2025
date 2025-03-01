# Hello Seaborn

## Inicializacion del proyecto
```python
import pandas as pd
pd.plotting.register_matplotlib_converters()
import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns
```

## Importar los datos
```python
fifa_filepath = "../input/fifa.csv

#Leer los datos
fifa_data = pd.read_csv(fifa_filepath, index_col = "Date", parse_dates = True)
```

## Crear una figura
```python
#Se determina el ancho y alto de la figura
plt.figure(figsize=(16,6))

# Grafico de la evolucion de los rankings FIFA
sns.lineplot(data=fifa_data)
```