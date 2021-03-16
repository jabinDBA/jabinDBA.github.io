---
title: "Dropping duplicates"
layout: single

categories:
  - Python
tags:
  - Python
  - Pandas
  - Drop duplicates
---

# Remove Duplicate

## Should we remove duplicates from a dataset?

Yes. Why?

- Duplicates are an extreme case of nonrandom sampling, and they bias your fitted model. 
- Including them will essentially lead to the model overfitting this subset of points.

## How?

1. Check duplicated rows
    - By using __pandas.DataFrame.duplicated__
    - It returns boolean Series denoting duplicate rows.
    - More Details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.duplicated.html#pandas-dataframe-duplicated


2. Get rid of the duplicates
    - By using __pandas.DataFrame.drop_duplicates__
    - It returns DataFrame with duplicate rows removed.
    - More Details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.drop_duplicates.html

Let's take a look at the following example.


```python
import pandas as pd

student_list = [
    {'name': 'John', 'major': "Computer Science", 'sex': "male"},
    {'name': 'Nate', 'major': "Computer Science", 'sex': "male"},
    {'name': 'Abraham', 'major': "Physics", 'sex': "male"},
    {'name': 'Brian', 'major': "Psychology", 'sex': "male"},
    {'name': 'Janny', 'major': "Economics", 'sex': "female"},
    {'name': 'Yuna', 'major': "Economics", 'sex': "female"},
    {'name': 'Jeniffer', 'major': "Computer Science", 'sex': "female"},
    {'name': 'Edward', 'major': "Computer Science", 'sex': "male"},
    {'name': 'Zara', 'major': "Psychology", 'sex': "female"},
    {'name': 'Wendy', 'major': "Economics", 'sex': "female"},
    {'name': 'Sera', 'major': "Psychology", 'sex': "female"},
    {'name': 'John', 'major': "Computer Science", 'sex': "male"}
]

df = pd.DataFrame(student_list)
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
      <th>major</th>
      <th>sex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nate</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Abraham</td>
      <td>Physics</td>
      <td>male</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Brian</td>
      <td>Psychology</td>
      <td>male</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Janny</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Yuna</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jeniffer</td>
      <td>Computer Science</td>
      <td>female</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Edward</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Zara</td>
      <td>Psychology</td>
      <td>female</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Wendy</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Sera</td>
      <td>Psychology</td>
      <td>female</td>
    </tr>
    <tr>
      <th>11</th>
      <td>John</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Check the duplicated rows

df.duplicated()
```




    0     False
    1     False
    2     False
    3     False
    4     False
    5     False
    6     False
    7     False
    8     False
    9     False
    10    False
    11     True
    dtype: bool



Now, we can see 'John' is the duplicated data.


```python
# Get rid of the duplicates

df = df.drop_duplicates()
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
      <th>major</th>
      <th>sex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nate</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Abraham</td>
      <td>Physics</td>
      <td>male</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Brian</td>
      <td>Psychology</td>
      <td>male</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Janny</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Yuna</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jeniffer</td>
      <td>Computer Science</td>
      <td>female</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Edward</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Zara</td>
      <td>Psychology</td>
      <td>female</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Wendy</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Sera</td>
      <td>Psychology</td>
      <td>female</td>
    </tr>
  </tbody>
</table>
</div>



You can see the last 'John' has been removed from the dataframe.

Let's see another example below.


```python
student_list = [{'name': 'John', 'major': "Computer Science", 'sex': "male"},
                {'name': 'Nate', 'major': "Computer Science", 'sex': "male"},
                {'name': 'Abraham', 'major': "Physics", 'sex': "male"},
                {'name': 'Brian', 'major': "Psychology", 'sex': "male"},
                {'name': 'Janny', 'major': "Economics", 'sex': "female"},
                {'name': 'Yuna', 'major': "Economics", 'sex': "female"},
                {'name': 'Jeniffer', 'major': "Computer Science", 'sex': "female"},
                {'name': 'Edward', 'major': "Computer Science", 'sex': "male"},
                {'name': 'Zara', 'major': "Psychology", 'sex': "female"},
                {'name': 'Wendy', 'major': "Economics", 'sex': "female"},
                {'name': 'Nate', 'major': None, 'sex': "male"},
                {'name': 'John', 'major': "Computer Science", 'sex': None},
         ]
```


```python
df = pd.DataFrame(student_list)
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
      <th>major</th>
      <th>sex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nate</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Abraham</td>
      <td>Physics</td>
      <td>male</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Brian</td>
      <td>Psychology</td>
      <td>male</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Janny</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Yuna</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jeniffer</td>
      <td>Computer Science</td>
      <td>female</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Edward</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Zara</td>
      <td>Psychology</td>
      <td>female</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Wendy</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Nate</td>
      <td>None</td>
      <td>male</td>
    </tr>
    <tr>
      <th>11</th>
      <td>John</td>
      <td>Computer Science</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Check duplicates based on 'name' column

df.duplicated(['name'])
```




    0     False
    1     False
    2     False
    3     False
    4     False
    5     False
    6     False
    7     False
    8     False
    9     False
    10     True
    11     True
    dtype: bool




```python
# Get rid of the duplicates.
# If you want to keep the last data and remove the first duplicates,

df = df.drop_duplicates(['name'], keep = 'last')
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
      <th>name</th>
      <th>major</th>
      <th>sex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Abraham</td>
      <td>Physics</td>
      <td>male</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Brian</td>
      <td>Psychology</td>
      <td>male</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Janny</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Yuna</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jeniffer</td>
      <td>Computer Science</td>
      <td>female</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Edward</td>
      <td>Computer Science</td>
      <td>male</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Zara</td>
      <td>Psychology</td>
      <td>female</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Wendy</td>
      <td>Economics</td>
      <td>female</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Nate</td>
      <td>None</td>
      <td>male</td>
    </tr>
    <tr>
      <th>11</th>
      <td>John</td>
      <td>Computer Science</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
</div>



Now, you can see 0, 1 indexed rows have been removed. On the other hand, you keep the last two rows (index 10 and 11).


```python

```
