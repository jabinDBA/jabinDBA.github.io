---
title: "Indexing and Selecting data"

categories:
  - Python
tags:
  - Python
  - Pandas
  - Indexing and Selecting data
---

# Indexing and Selecting data

## Select Row

### by index

Let's import panadas and make a dataframe first


```python
import pandas as pd
```


```python
employee_dict = [
    {'name': 'John', 'age': 23, 'job': 'developer'},
    {'name': 'James', 'age': 33, 'job': 'data analyst'},
    {'name': 'Raymond', 'age': 35, 'job': 'accountant'},
    {'name': 'Edward', 'age': 56, 'job': 'mechanical engineer'},
]

df = pd.DataFrame.from_dict(employee_dict)
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>23</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>James</td>
      <td>33</td>
      <td>data analyst</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Raymond</td>
      <td>35</td>
      <td>accountant</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Edward</td>
      <td>56</td>
      <td>mechanical engineer</td>
    </tr>
  </tbody>
</table>
</div>



Select rows from index 1 to 2


```python
df[1:3]
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>James</td>
      <td>33</td>
      <td>data analyst</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Raymond</td>
      <td>35</td>
      <td>accountant</td>
    </tr>
  </tbody>
</table>
</div>



Select rows - index 0 and 3 only


```python
# pandas.DataFrame.loc
# Access a group of rows and columns

df.loc[[0,3]]
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>23</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Edward</td>
      <td>56</td>
      <td>mechanical engineer</td>
    </tr>
  </tbody>
</table>
</div>



### by column condition

Select rows by column condition

Select employees older than 25


```python
df_greater_than_25 = df[df.age > 25]

df_greater_than_25
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>James</td>
      <td>33</td>
      <td>data analyst</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Raymond</td>
      <td>35</td>
      <td>accountant</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Edward</td>
      <td>56</td>
      <td>mechanical engineer</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Here is another way :
# pandas.DataFrame.query(str)

df_greater_than_25 = df.query('age > 25')
df_greater_than_25
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>James</td>
      <td>33</td>
      <td>data analyst</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Raymond</td>
      <td>35</td>
      <td>accountant</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Edward</td>
      <td>56</td>
      <td>mechanical engineer</td>
    </tr>
  </tbody>
</table>
</div>



Select employees who is older than 25 AND is a data analyst


```python
df_filtered = df[(df.age>25) & (df.job == 'data analyst')]
df_filtered
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>James</td>
      <td>33</td>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>



## Select Column
### by index


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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>23</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>James</td>
      <td>33</td>
      <td>data analyst</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Raymond</td>
      <td>35</td>
      <td>accountant</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Edward</td>
      <td>56</td>
      <td>mechanical engineer</td>
    </tr>
  </tbody>
</table>
</div>



Select the name and age column


```python
# pandas.DataFrame.iloc()
# Purely integer-location based indexing for selection by position
df.iloc[:, 0:2]
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
      <th>age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>23</td>
    </tr>
    <tr>
      <th>1</th>
      <td>James</td>
      <td>33</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Raymond</td>
      <td>35</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Edward</td>
      <td>56</td>
    </tr>
  </tbody>
</table>
</div>



Select the name and job column


```python
df.iloc[:, [0,2]]
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>James</td>
      <td>data analyst</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Raymond</td>
      <td>accountant</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Edward</td>
      <td>mechanical engineer</td>
    </tr>
  </tbody>
</table>
</div>



### by column name

Select the name and age column


```python
df_filtered = df[['name', 'age']]
df_filtered
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
      <th>age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>23</td>
    </tr>
    <tr>
      <th>1</th>
      <td>James</td>
      <td>33</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Raymond</td>
      <td>35</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Edward</td>
      <td>56</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Here is another way :
# pandas.DataFrame.filter()
# Subset the dataframe rows or columns according to the specified index labels.

df.filter(items=['name', 'job'])
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>James</td>
      <td>data analyst</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Raymond</td>
      <td>accountant</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Edward</td>
      <td>mechanical engineer</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
