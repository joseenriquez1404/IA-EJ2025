# Seasonality

```python
X = tunnel.copy()

#Days within a week
X["day"] = X.index.dayofweek # The x-axis (freq)
X["week"] = X.index.week # The seasonal period

X["dayofyear"] = X.index_dayofyear
X["year"] = X.index.year
fig, (ax0, ax1) = plt.subplots(2, 1, figsize = (11, 6))
seasonal_plot(X, y = "NumVehicles", period = "week", freq = "day", ax = ax0)
seasonal_plot(X, y = "NumVehicles", period = "year", freq = "dayofyear", ax = ax1)
```

```python
from statsmodels.tsa.deterministic import CalendarFourier, DeterministicProcess

fourier = CalendarFourier(freq="A", order=10)  # 10 sin/cos pairs for "A"nnual seasonality

dp = DeterministicProcess(
    index=tunnel.index,
    constant=True,               # dummy feature for bias (y-intercept)
    order=1,                     # trend (order 1 means linear)
    seasonal=True,               # weekly seasonality (indicators)
    additional_terms=[fourier],  # annual seasonality (fourier)
    drop=True,                   # drop terms to avoid collinearity
)

X = dp.in_sample()  # create features for dates in tunnel.index
```