# Permutation Importance

- **Feature importance** es la pregunta de cuales features tienen un mayor impacto en las predicciones.

- Permutation importance
    - Rapido de calcular
    - Muy usado
    - Consistente con las propiedades que queremos que el feature importance tenga.
    
El proceso para realizar un permutation importance
1. Obtener un modelo entrenado
2. Barajear los valores de una columna y crear predicciones usando el dataset revuelto, con estas prediccione y el verdadero target ver como se vio afectado el resultado.
3. Volver al dataset original y repetir el paso 2 con la siguiente columna

Ejemplo: Queremos ver que jugador va a optener el "MVP"

Cargamos el dataset y se crea un modelo básico
```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier

data = pd.read_csv('../input/fifa-2018-match-statistics/FIFA 2018 Statistics.csv')
y = (data['Man of the Match'] == "Yes")  # Convert from string "Yes"/"No" to binary
feature_names = [i for i in data.columns if data[i].dtype in [np.int64]]
X = data[feature_names]
train_X, val_X, train_y, val_y = train_test_split(X, y, random_state=1)
my_model = RandomForestClassifier(n_estimators=100,
                                  random_state=0).fit(train_X, train_y)
```

Aqui se aplica el permutation importance
```python
import eli5
from eli5.sklearn import PermutationImportance

perm = PermutationImportance(my_model, random_state=1).fit(val_X, val_y)
eli5.show_weights(perm, feature_names = val_X.columns.tolist())
```
