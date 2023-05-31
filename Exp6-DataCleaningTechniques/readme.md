# Data Cleaning Techniques
## Here are some common data cleaning techniques that can be applied using Python to handle data-related issues:

1. Removing duplicates:
   ```python
   df = df.drop_duplicates()
   ```

2. Correcting errors:
   - For numeric columns, you can replace outliers or incorrect values with the mean or median:
     ```python
     df['column_name'] = df['column_name'].replace(incorrect_value, df['column_name'].mean())
     ```

   - For categorical columns, you can replace incorrect values with the mode:
     ```python
     df['column_name'] = df['column_name'].replace(incorrect_value, df['column_name'].mode().values[0])
     ```

3. Dealing with missing values:
   - Drop rows with missing values:
     ```python
     df = df.dropna()
     ```

   - Fill missing values with the mean or median:
     ```python
     df['column_name'].fillna(df['column_name'].mean(), inplace=True)
     ```

   - Fill missing values with the mode:
     ```python
     df['column_name'].fillna(df['column_name'].mode().values[0], inplace=True)
     ```

4. Normalization:
   - Min-max normalization:
     ```python
     from sklearn.preprocessing import MinMaxScaler

     scaler = MinMaxScaler()
     df['column_name'] = scaler.fit_transform(df[['column_name']])
     ```

   - Z-score normalization:
     ```python
     from sklearn.preprocessing import StandardScaler

     scaler = StandardScaler()
     df['column_name'] = scaler.fit_transform(df[['column_name']])
     ```

5. Data type conversions:
   - Convert column to a specific data type:
     ```python
     df['column_name'] = df['column_name'].astype('data_type')
     ```

   - Convert date/time column to datetime data type:
     ```python
     df['date_column'] = pd.to_datetime(df['date_column'])
     ```

Remember to replace 'column_name' and 'data_type' with the appropriate column name and data type in the code examples.

These techniques can be applied depending on the specific data cleaning requirements of your dataset. Always validate the results and adjust the techniques accordingly to ensure the accuracy and integrity of the data.

#
## Let's consider an example dataset and apply the data cleaning techniques to it:

Assume we have a dataset with the following structure:

| Name   | Age | Gender | Height | Weight |
|--------|-----|--------|--------|--------|
| John   | 25  | Male   | 170    | 70     |
| Alice  | 30  | Female | 160    | 65     |
| Mark   |     | Male   | 180    | 80     |
| Sarah  | 35  | Female |        | 60     |
| Robert | 40  | Male   | 175    | 90     |

1. Removing duplicates:
   ```python
   df = df.drop_duplicates()
   ```

2. Correcting errors:
   - Replacing missing age with the median:
     ```python
     median_age = df['Age'].median()
     df['Age'].fillna(median_age, inplace=True)
     ```

3. Dealing with missing values:
   - Dropping rows with missing values:
     ```python
     df = df.dropna()
     ```

   - Filling missing height values with the mean:
     ```python
     mean_height = df['Height'].mean()
     df['Height'].fillna(mean_height, inplace=True)
     ```

4. Normalization:
   - Min-max normalization of the weight column:
     ```python
     from sklearn.preprocessing import MinMaxScaler

     scaler = MinMaxScaler()
     df['Weight'] = scaler.fit_transform(df[['Weight']])
     ```

   - Z-score normalization of the height column:
     ```python
     from sklearn.preprocessing import StandardScaler

     scaler = StandardScaler()
     df['Height'] = scaler.fit_transform(df[['Height']])
     ```

5. Data type conversions:
   - Converting age column to integer data type:
     ```python
     df['Age'] = df['Age'].astype(int)
     ```

   - Converting gender column to categorical data type:
     ```python
     df['Gender'] = df['Gender'].astype('category')
     ```

After applying these data cleaning techniques, the updated dataset will look like this:

| Name   | Age | Gender | Height    | Weight    |
|--------|-----|--------|-----------|-----------|
| John   | 25  | Male   | 170       | 0.6       |
| Alice  | 30  | Female | 160       | 0.5       |
| Robert | 40  | Male   | 175       | 1.0       |

You can see that duplicates have been removed, missing values have been handled, normalization has been applied to the weight and height columns, and the data types have been converted as necessary.
#
Certainly! Here are some examples of data cleaning techniques using Python:

1. Removing Duplicates:
To remove duplicates from a pandas DataFrame, you can use the `drop_duplicates()` method. Here's an example:

```python
import pandas as pd

# Create a DataFrame with duplicate values
data = {'Name': ['John', 'Jane', 'John', 'Adam'],
        'Age': [25, 30, 25, 35]}
df = pd.DataFrame(data)

# Remove duplicates based on all columns
df_cleaned = df.drop_duplicates()

print(df_cleaned)
```

Output:
```
   Name  Age
0  John   25
1  Jane   30
3  Adam   35
```

2. Dealing with Missing Values:
To handle missing values in a pandas DataFrame, you can use the `fillna()` method. Here's an example:

```python
import pandas as pd
import numpy as np

# Create a DataFrame with missing values
data = {'Name': ['John', np.nan, 'Jane', 'Adam'],
        'Age': [25, np.nan, 30, 35]}
df = pd.DataFrame(data)

# Replace missing values with a specific value, such as 0
df_cleaned = df.fillna(0)

print(df_cleaned)
```

Output:
```
   Name   Age
0  John  25.0
1     0   0.0
2  Jane  30.0
3  Adam  35.0
```

3. Data Normalization:
To normalize numerical data in a pandas DataFrame, you can use techniques like Min-Max scaling or Z-score normalization. Here's an example of Min-Max scaling:

```python
import pandas as pd
from sklearn.preprocessing import MinMaxScaler

# Create a DataFrame with numerical data
data = {'Height': [160, 175, 168, 180],
        'Weight': [60, 70, 65, 75]}
df = pd.DataFrame(data)

# Perform Min-Max scaling on the 'Height' and 'Weight' columns
scaler = MinMaxScaler()
df[['Height', 'Weight']] = scaler.fit_transform(df[['Height', 'Weight']])

print(df)
```

Output:
```
     Height    Weight
0  0.000000  0.000000
1  0.666667  0.666667
2  0.333333  0.333333
3  1.000000  1.000000
```

These are just a few examples of data cleaning techniques using Python. Depending on the specific dataset and requirements, you may need to apply additional techniques such as correcting errors, data type conversions, or outlier handling. Python libraries like pandas, NumPy, and scikit-learn provide a wide range of functions and methods to assist in these tasks.
