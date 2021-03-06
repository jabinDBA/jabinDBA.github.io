---
title: "Create a DataFrame"

categories:
  - Python
tags:
  - Python
  - Pandas
  - Data Frame
---

# What is DataFrame?

Dataframe is a 2-dimensional labeled data structure with columns

# How to create a dataframe?

You can create a dataframe in one of the following ways :

1. from dictionary
2. from ordered dictionary
3. from list

## from dictionary

### What is dictionary?
Dictionaries are used to store data values in key:value pairs.
Dictionaries are written with curly brackets.

(Example)    
```python
thisdict = {
 "brand": "Ford",
 "model": "Mustang",
 "year": 1964
}
```



```python
import pandas as pd

friend_dict_list = [
    {'name': 'Jone', 'age': 20, 'job': 'student'},
    {'name': 'Jenny', 'age': 30, 'job': 'teacher'},
    {'name': 'Smith', 'age': 26, 'job': 'data analyst'}
]
```


```python
df = pd.DataFrame(friend_dict_list)
df.head()
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
      <td>Jone</td>
      <td>20</td>
      <td>student</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jenny</td>
      <td>30</td>
      <td>teacher</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Smith</td>
      <td>26</td>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>




```python
# If you want to re-order the column,
df = df[['age', 'name', 'job']]
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
      <th>name</th>
      <th>job</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20</td>
      <td>Jone</td>
      <td>student</td>
    </tr>
    <tr>
      <th>1</th>
      <td>30</td>
      <td>Jenny</td>
      <td>teacher</td>
    </tr>
    <tr>
      <th>2</th>
      <td>26</td>
      <td>Smith</td>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>



## from Ordered Dictionary
### What is an ordered dictionary?
- An OrderedDict is a dictionary subclass that remembers the order that keys were first inserted.
- A regular dict doesn’t track the insertion order, but an OrderedDict does.


```python
# First, you need to import OrderedDict from collections
from collections import OrderedDict
```


```python
friend_ordered_dict = OrderedDict(
    [
        ('name', ['John', 'Jenny', 'Smith']),
        ('age', [20, 30, 26]),
        ('job', ['student', 'teacher', 'data analyst']),
    ]
)
```


```python
# pandas.DataFrame.from_dict
# See Details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.from_dict.html
df = pd.DataFrame.from_dict(friend_ordered_dict)
df.head()
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
      <td>20</td>
      <td>student</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jenny</td>
      <td>30</td>
      <td>teacher</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Smith</td>
      <td>26</td>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>



## from list
### What is a list?
A list is a data structure in Python that is a mutable, or changeable, ordered sequence of elements.

(Example)
```python
sea_creatures = ['shark', 'cuttlefish', 'squid', 'mantis shrimp', 'anemone']


```



```python
# Create a list
friend_list = [
    ['John', 20, 'student'],
    ['Jenny', 30, 'teacher'],
    ['Smith', 26, 'data analyst'],
]
```


```python
# Define a header name (column)
col_name = ['name', 'age', 'job']
```


```python
# pandas.DataFrame.from_record()
# See Details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.from_records.html?highlight=pandas%20dataframe%20from_records#pandas.DataFrame.from_records
df = pd.DataFrame.from_records(friend_list, columns = col_name)
df.head()
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
      <td>20</td>
      <td>student</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jenny</td>
      <td>30</td>
      <td>teacher</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Smith</td>
      <td>26</td>
      <td>data analyst</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
