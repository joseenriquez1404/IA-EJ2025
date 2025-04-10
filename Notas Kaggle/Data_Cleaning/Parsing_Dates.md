# Parsing Dates
Primero preparamos las librerias
```python
# modules we'll use
import pandas as pd
import numpy as np
import seaborn as sns
import datetime

# read in our data
landslides = pd.read_csv("../input/landslide-events/catalog.csv")

# set seed for reproducibility
np.random.seed(0)
```

Convertir la fecha a modo fecha
```python
landslides['date_parsed'] = pd.to_datetime(landslides['date'], format="%m/%d/%y")
```