# Data Visualization

To visualize data and perform exploratory analysis, you can use various Python libraries, such as Matplotlib, Seaborn, and Plotly. Here are some common visualization techniques to detect relationships between variables:

1. Scatter Plot:
A scatter plot is useful for visualizing the relationship between two continuous variables. Each point represents a data point, and the position of the point on the x-y axes corresponds to the values of the two variables. Matplotlib and Seaborn provide functions to create scatter plots. Here's an example using Matplotlib:

```python
import matplotlib.pyplot as plt

# Create a scatter plot
x = [1, 2, 3, 4, 5]
y = [2, 4, 5, 7, 8]
plt.scatter(x, y)
plt.xlabel('X')
plt.ylabel('Y')
plt.title('Scatter Plot')
plt.show()
```

2. Line Plot:
A line plot is useful for visualizing the trend or pattern of a variable over a continuous axis, such as time. It can help identify trends, seasonality, or patterns in the data. Matplotlib and Seaborn can be used to create line plots. Here's an example using Matplotlib:

```python
import matplotlib.pyplot as plt

# Create a line plot
x = [1, 2, 3, 4, 5]
y = [2, 4, 5, 7, 8]
plt.plot(x, y)
plt.xlabel('X')
plt.ylabel('Y')
plt.title('Line Plot')
plt.show()
```

3. Histogram:
A histogram is useful for visualizing the distribution of a single variable. It shows the frequency or count of values within specific bins or intervals. Matplotlib and Seaborn can be used to create histograms. Here's an example using Matplotlib:

```python
import matplotlib.pyplot as plt

# Create a histogram
data = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4, 5, 5]
plt.hist(data, bins=5)
plt.xlabel('Values')
plt.ylabel('Frequency')
plt.title('Histogram')
plt.show()
```

4. Heatmap:
A heatmap is useful for visualizing the relationship between two categorical variables. It displays the frequencies or values of a variable in a grid, with different colors representing the values. Seaborn provides a heatmap function. Here's an example:

```python
import seaborn as sns
import pandas as pd

# Create a DataFrame
data = {'Category': ['A', 'A', 'B', 'B', 'C', 'C'],
        'Variable': ['X', 'Y', 'X', 'Y', 'X', 'Y'],
        'Value': [1, 2, 3, 4, 5, 6]}
df = pd.DataFrame(data)

# Create a heatmap
pivot_table = df.pivot(index='Category', columns='Variable', values='Value')
sns.heatmap(pivot_table, annot=True, cmap='YlGnBu')
plt.title('Heatmap')
plt.show()
```


5. Bar Plot:
A bar plot is useful for comparing categorical variables or showing the distribution of a variable across different categories. Matplotlib and Seaborn can be used to create bar plots. Here's an example using Seaborn:

```python
import seaborn as sns

# Create a bar plot
data = {'Category': ['A', 'B', 'C', 'D'],
        'Value': [10, 15, 7, 12]}
df = pd.DataFrame(data)

sns.barplot(x='Category', y='Value', data=df)
plt.xlabel('Category')
plt.ylabel('Value')
plt.title('Bar Plot')
plt.show()
```

6. Box Plot:
A box plot is useful for visualizing the distribution of a continuous variable across different categories or groups. It shows the median, quartiles, and potential outliers. Matplotlib and Seaborn can be used to create box plots. Here's an example using Matplotlib:

```python
import matplotlib.pyplot as plt

# Create a box plot
data = {'Category': ['A', 'A', 'B', 'B', 'B', 'C', 'C'],
        'Value': [10, 15, 7, 12, 20, 5, 18]}
df = pd.DataFrame(data)

plt.boxplot([df[df['Category'] == 'A']['Value'],
             df[df['Category'] == 'B']['Value'],
             df[df['Category'] == 'C']['Value']],
            labels=['A', 'B', 'C'])
plt.xlabel('Category')
plt.ylabel('Value')
plt.title('Box Plot')
plt.show()
```

7. Violin Plot:
A violin plot combines aspects of a box plot and a kernel density plot to show the distribution of a continuous variable across different categories. It provides a visual representation of the data density. Seaborn can be used to create violin plots. Here's an example:

```python
import seaborn as sns

# Create a violin plot
data = {'Category': ['A', 'A', 'B', 'B', 'B', 'C', 'C'],
        'Value': [10, 15, 7, 12, 20, 5, 18]}
df = pd.DataFrame(data)

sns.violinplot(x='Category', y='Value', data=df)
plt.xlabel('Category')
plt.ylabel('Value')
plt.title('Violin Plot')
plt.show()
```

8. Pair Plot:
A pair plot is useful for visualizing relationships between multiple variables in a dataset. It displays scatter plots for each pair of variables and distributions on the diagonal. Seaborn provides a pair plot function. Here's an example:

```python
import seaborn as sns

# Create a pair plot
data = {'Feature1': [1, 2, 3, 4, 5],
        'Feature2': [2, 4, 5, 7, 8],
        'Feature3': [3, 6, 9, 12, 15]}
df = pd.DataFrame(data)

sns.pairplot(df)
plt.show()
```

9. Area Plot:
   Area plots are useful for visualizing the trend and proportion of different categories over time or any other continuous variable.

   ```python
   import pandas as pd
   import matplotlib.pyplot as plt

   # Create a sample dataset
   data = {'Year': [2010, 2011, 2012, 2013, 2014],
           'Category A': [10, 15, 25, 20, 30],
           'Category B': [20, 25, 15, 30, 10],
           'Category C': [30, 20, 10, 15, 25]}

   df = pd.DataFrame(data)

   # Plot area chart
   plt.stackplot(df['Year'], df['Category A'], df['Category B'], df['Category C'],
                 labels=['Category A', 'Category B', 'Category C'], alpha=0.8)

   plt.xlabel('Year')
   plt.ylabel('Value')
   plt.title('Area Plot')
   plt.legend()
   plt.show()
   ```

10. Stacked Bar Plot:
   Stacked bar plots are useful for visualizing the distribution and comparison of different categories.

   ```python
   import pandas as pd
   import matplotlib.pyplot as plt

   # Create a sample dataset
   data = {'Year': [2010, 2011, 2012, 2013, 2014],
           'Category A': [10, 15, 25, 20, 30],
           'Category B': [20, 25, 15, 30, 10],
           'Category C': [30, 20, 10, 15, 25]}

   df = pd.DataFrame(data)

   # Plot stacked bar chart
   plt.bar(df['Year'], df['Category A'], label='Category A')
   plt.bar(df['Year'], df['Category B'], bottom=df['Category A'], label='Category B')
   plt.bar(df['Year'], df['Category C'], bottom=df['Category A']+df['Category B'], label='Category C')

   plt.xlabel('Year')
   plt.ylabel('Value')
   plt.title('Stacked Bar Plot')
   plt.legend()
   plt.show()
   ```

11. Correlation Plot:
   Correlation plots are useful for visualizing the correlation between different variables in a dataset.

   ```python
   import pandas as pd
   import seaborn as sns
   import matplotlib.pyplot as plt

   # Create a sample dataset
   data = {'Variable 1': [1, 2, 3, 4, 5],
           'Variable 2': [5, 4, 3, 2, 1],
           'Variable 3': [3, 2, 1, 4, 5],
           'Variable 4': [1, 1, 1, 1, 1]}

   df = pd.DataFrame(data)

   # Calculate correlation matrix
   corr_matrix = df.corr()

   # Plot correlation matrix as a heatmap
   plt.figure(figsize=(8, 6))
   sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')

   plt.title('Correlation Plot')
   plt.show()
   ```
