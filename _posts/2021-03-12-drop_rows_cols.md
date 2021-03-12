---
title: "Remove rows or columns"
layout: single

categories:
  - Python
tags:
  - Python
  - Pandas
  - Drop data
---


# Remove rows or columns

We are going to drop specified labels from rows or columns in this chapter.

## Drop rows by row name - index name

Let's make a data frame for an example.


```python
import pandas as pd

employee_list = [
    {'age': 20, 'job': 'student'},
    {'age': 34, 'job': 'sales manager'},
    {'age': 26, 'job': 'developer'},
    {'age': 49, 'job': 'director'},
    {'age': 31, 'job': 'data analyst'},
]

df = pd.DataFrame(employee_list, index = ['John', 'Nate', 'Mathew', 'James', 'Mike'])
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>John</th>
      <td>20</td>
      <td>student</td>
    </tr>
    <tr>
      <th>Nate</th>
      <td>34</td>
      <td>sales manager</td>
    </tr>
    <tr>
      <th>Mathew</th>
      <td>26</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>James</th>
      <td>49</td>
      <td>director</td>
    </tr>
    <tr>
      <th>Mike</th>
      <td>31</td>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>



Drop all rows except for James


```python
df.drop(['John', 'Nate', 'Mathew', 'Mike'])
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>James</th>
      <td>49</td>
      <td>director</td>
    </tr>
  </tbody>
</table>
</div>



NOTE : The dataframe still remains as follows :


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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>John</th>
      <td>20</td>
      <td>student</td>
    </tr>
    <tr>
      <th>Nate</th>
      <td>34</td>
      <td>sales manager</td>
    </tr>
    <tr>
      <th>Mathew</th>
      <td>26</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>James</th>
      <td>49</td>
      <td>director</td>
    </tr>
    <tr>
      <th>Mike</th>
      <td>31</td>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>



If you don't want to keep all data after dropping the rows,


```python
df.drop(['John', 'Nate', 'Mathew', 'Mike'], inplace = True)
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>James</th>
      <td>49</td>
      <td>director</td>
    </tr>
  </tbody>
</table>
</div>




```python
employee_list = [
    {'age': 20, 'job': 'student'},
    {'age': 34, 'job': 'sales manager'},
    {'age': 26, 'job': 'developer'},
    {'age': 49, 'job': 'director'},
    {'age': 31, 'job': 'data analyst'},
]

df = pd.DataFrame(employee_list, index = ['John', 'Nate', 'Mathew', 'James', 'Mike'])
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>John</th>
      <td>20</td>
      <td>student</td>
    </tr>
    <tr>
      <th>Nate</th>
      <td>34</td>
      <td>sales manager</td>
    </tr>
    <tr>
      <th>Mathew</th>
      <td>26</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>James</th>
      <td>49</td>
      <td>director</td>
    </tr>
    <tr>
      <th>Mike</th>
      <td>31</td>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>



You can drop rows by index number as well


```python
df = df.drop(df.index[[0,1,2,4]])
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>James</th>
      <td>49</td>
      <td>director</td>
    </tr>
  </tbody>
</table>
</div>



## Drop columns by conditions

Let's say we have the same data


```python
employee_list = [
    {'age': 20, 'job': 'student'},
    {'age': 34, 'job': 'sales manager'},
    {'age': 26, 'job': 'developer'},
    {'age': 49, 'job': 'director'},
    {'age': 31, 'job': 'data analyst'},
]

df = pd.DataFrame(employee_list, index = ['John', 'Nate', 'Mathew', 'James', 'Mike'])
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>John</th>
      <td>20</td>
      <td>student</td>
    </tr>
    <tr>
      <th>Nate</th>
      <td>34</td>
      <td>sales manager</td>
    </tr>
    <tr>
      <th>Mathew</th>
      <td>26</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>James</th>
      <td>49</td>
      <td>director</td>
    </tr>
    <tr>
      <th>Mike</th>
      <td>31</td>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>



Delete all rows which is not at age of 34


```python
df = df[df.age == 34]
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Nate</th>
      <td>34</td>
      <td>sales manager</td>
    </tr>
  </tbody>
</table>
</div>



## Drop columns


```python
employee_list = [
    {'age': 20, 'job': 'student'},
    {'age': 34, 'job': 'sales manager'},
    {'age': 26, 'job': 'developer'},
    {'age': 49, 'job': 'director'},
    {'age': 31, 'job': 'data analyst'},
]

df = pd.DataFrame(employee_list, index = ['John', 'Nate', 'Mathew', 'James', 'Mike'])
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
      <th>age</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>John</th>
      <td>20</td>
      <td>student</td>
    </tr>
    <tr>
      <th>Nate</th>
      <td>34</td>
      <td>sales manager</td>
    </tr>
    <tr>
      <th>Mathew</th>
      <td>26</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>James</th>
      <td>49</td>
      <td>director</td>
    </tr>
    <tr>
      <th>Mike</th>
      <td>31</td>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>



Drop the 'age' column


```python
df = df.drop('age', axis=1)    # axis=0 : row, axis=1 : column
```


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
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>John</th>
      <td>student</td>
    </tr>
    <tr>
      <th>Nate</th>
      <td>sales manager</td>
    </tr>
    <tr>
      <th>Mathew</th>
      <td>developer</td>
    </tr>
    <tr>
      <th>James</th>
      <td>director</td>
    </tr>
    <tr>
      <th>Mike</th>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>



Reference : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.drop.html


```python

```
