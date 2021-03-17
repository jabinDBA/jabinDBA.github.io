# Handling Missing Values

- Python libraries represent missing numbers as nan which is short for "not a number".
- You should detect which cells have missing values and fill them with something else.

Let's say we have the following dataframe :


```python
import pandas as pd

students_list = [
    {'name': 'John', 'job': "teacher", 'age': 40},
    {'name': 'Nate', 'job': "teacher", 'age': 35},
    {'name': 'Yuna', 'job': "teacher", 'age': 37},
    {'name': 'Abraham', 'job': "student", 'age': 10},
    {'name': 'Brian', 'job': "student", 'age': 12},
    {'name': 'Janny', 'job': "student", 'age': 11},
    {'name': 'Nate', 'job': "teacher", 'age': None},
    {'name': 'John', 'job': "student", 'age': None}
]

df = pd.DataFrame(students_list)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>job</th>
      <th>age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>teacher</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nate</td>
      <td>teacher</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Yuna</td>
      <td>teacher</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abraham</td>
      <td>student</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Brian</td>
      <td>student</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Janny</td>
      <td>student</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Nate</td>
      <td>teacher</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>John</td>
      <td>student</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



The above dataset involves 'NaN' value - the last two rows

## How to defect missing values?

You can usd __pandas.DataFrame.isna()__ to detect missing values.

- It returns a boolean same-sized object indicating if the values are NA - such as None or NaN (gets mapped to __True__ values)
- More Details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.isna.html


```python
df.isna()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>job</th>
      <th>age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>5</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>6</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.isnull()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>job</th>
      <th>age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>5</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>6</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



## How to fill missing values with something else?

Use __pandas.DataFrame.fillna()__ method.

- This fills NA/NaN values using the specified method.
- More Details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.fillna.html

Let's see the following example :


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>job</th>
      <th>age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>teacher</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nate</td>
      <td>teacher</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Yuna</td>
      <td>teacher</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abraham</td>
      <td>student</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Brian</td>
      <td>student</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Janny</td>
      <td>student</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Nate</td>
      <td>teacher</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>John</td>
      <td>student</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Fill missing values with '0'
df['age'] = df['age'].fillna(0)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>job</th>
      <th>age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>teacher</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nate</td>
      <td>teacher</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Yuna</td>
      <td>teacher</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abraham</td>
      <td>student</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Brian</td>
      <td>student</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Janny</td>
      <td>student</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Nate</td>
      <td>teacher</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>John</td>
      <td>student</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>



In general, missing values are filled with a median.


```python
# pandas.DataFrame.transform(func) : Call func on self producing a DataFrame with transformed values.
# Details : https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.transform.html

value = df.groupby('job')['age'].transform('median')
value
```




    0    36.0
    1    36.0
    2    36.0
    3    10.5
    4    10.5
    5    10.5
    6    36.0
    7    10.5
    Name: age, dtype: float64




```python
df["age"].fillna(value)
```




    0    40.0
    1    35.0
    2    37.0
    3    10.0
    4    12.0
    5    11.0
    6     0.0
    7     0.0
    Name: age, dtype: float64




```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>job</th>
      <th>age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>teacher</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nate</td>
      <td>teacher</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Yuna</td>
      <td>teacher</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abraham</td>
      <td>student</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Brian</td>
      <td>student</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Janny</td>
      <td>student</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Nate</td>
      <td>teacher</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>John</td>
      <td>student</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
