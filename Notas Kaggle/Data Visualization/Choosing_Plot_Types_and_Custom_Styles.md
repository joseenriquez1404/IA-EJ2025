# Choosing Plot Types and Custom Styles

## Changing styles with seaborn
```python
# Change the style of the figure to the "dark" theme
sns.set_style("dark")

# Line chart 
plt.figure(figsize=(12,6))
sns.lineplot(data=spotify_data)
```