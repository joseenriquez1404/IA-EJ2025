# Stochastic Gradient Descent

Se crea el modelo

```python
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
    layers.Dense(512, activation='relu', input_shape=[11]),
    layers.Dense(512, activation='relu'),
    layers.Dense(512, activation='relu'),
    layers.Dense(1),
])
```

Luego se especifica el optimizador y la función loss
```python
model.compile(
    optimizer = 'adam', 
    loss = 'mae', 
)
```

Ahora se empieza el entrenamiento
```python
history = model.fit(
    X_train, y_train, 
    validation_data = (X_valid, y_valid), 
    batch_size = 256, #Se utilizan 256 filas de datos 
    epochs = 10, #Se repite 10 veces
)
```