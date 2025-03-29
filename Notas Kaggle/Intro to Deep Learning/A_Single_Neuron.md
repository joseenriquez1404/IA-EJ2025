# A Single Neuron

Para crear una neurona con un output y 3 inputs
```python
from tensorflow import keras
from tensorflow.keras import layers

# Create a network with 1 linear unit
model = keras.Sequential([
    layers.Dense(units=1, input_shape=[3])
])
```

Para aplicar los pesos al inicio
```python
w, b = model.weights
```