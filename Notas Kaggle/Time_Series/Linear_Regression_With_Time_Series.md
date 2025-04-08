# Linear Regression With Time Series

## Time Step feature
```python
df = tunnel.copy()

df['Time'] = np.arrange(len(tunnel.index))

df.head
```

```python
from sklearn.linear_model import LinearRegression

#Training Data
X = df.loc[:, ['Time']] # features
y = df.loc[:, 'NumVehicles'] #target

model = LinearRegression()
model.fit(X, y)

# Store the fitted values as a time series with the same time index as the training data
y_pred = pd.Series(model.predict(X), index = X.index)
```

## Lag feature
```python
df['Lag_1'] = df['NumVehicles'].shift(1)
df.head()
```

```python
from sklearn.linear_model import LinearRegression

X = df.loc[:, ['Lag_1']]
X.dropna(inplace = True) # Drop missing values in the feature set
y = df.loc[:, 'NumVehicles'] # Create the target
y, X = y.align(X, join = 'inner') # Drop corresponding values in target

model = LinearRegression()
model.fit(X, y)

y_pred = pd.Series(model.predict(X), index = X.index)
```