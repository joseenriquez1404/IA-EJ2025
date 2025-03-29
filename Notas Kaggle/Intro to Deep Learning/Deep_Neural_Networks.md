# Deep Neural Networks

Para crear capas de neuronas
```python
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
    # Las capas ocultas de ReLU
    layers.Dense(units = 4, activation = 'relu', input_shape = [2]),
    layers.Dense(units = 3, activation = 'relu'),
    # La capa de output
    layers.Dense(units = 1)
])
```