# Dropout and Batch Normalization

## Adding dropout
```python
keras.Sequential([
    # ...
    layers.Dropout(rate=0.3), # apply 30% dropout to the next layer
    layers.Dense(16),
    # ...
])
```

## Adding Batch Normalitazion

```python
layers.Dense(16, activation='relu'),
layers.BatchNormalization(),
```