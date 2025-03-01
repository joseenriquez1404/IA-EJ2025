# Distributions

## Histograms
```python
sns.histplot(iris_data['Petal Length (cm)'])
```

## Density plots
```python
sns.kdeplot(data=iris_data['Petal Length (cm)'], shade=True)
```

## 2D KDE plots
```python
sns.jointplot(x=iris_data['Petal Length (cm)'], y=iris_data['Sepal Width (cm)'], kind="kde")
```

## Color-coded plots
```python
# Histograms for each species
sns.histplot(data=iris_data, x='Petal Length (cm)', hue='Species')

# Add title
plt.title("Histogram of Petal Lengths, by Species")

# KDE plots for each species
sns.kdeplot(data=iris_data, x='Petal Length (cm)', hue='Species', shade=True)

# Add title
plt.title("Distribution of Petal Lengths, by Species")
```