# Scatter Plots

## Scatter Plots
```python
sns.scatterplot(x=insurance_data['bmi'], y=insurance_data['charges'])

sns.regplot(x=insurance_data['bmi'], y=insurance_data['charges'])
```

## Color-coded scatter plots
```python
sns.scatterplot(x=insurance_data['bmi'], y=insurance_data['charges'], hue=insurance_data['smoker'])

sns.lmplot(x="bmi", y="charges", hue="smoker", data=insurance_data)

sns.swarmplot(x=insurance_data['smoker'],
              y=insurance_data['charges'])
```

