---
title: "Export DataFrame to a csv file"

categories:
  - Python
tags:
  - Python
  - Pandas
  - Export DataFrame to csv
---

# How to export DataFrame to a csv file in Pandas?

- Use __pandas.DataFrame.to_csv()__ method.
- This writes object to a comma-separated values (csv) file.

More Details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_csv.html


```python
# First, import pandas package
import pandas as pd
```


```python
# Create a data frame from dictionary
people = [
    {'name': 'James', 'age': 32, 'job': 'developer'},
    {'name': 'Jenny', 'age': 24, 'job': 'web designer'},
    {'name': 'Pawl', 'age': 45, 'job': 'it manager'}
]

df = pd.DataFrame(people)
df = df[['name', 'age', 'job']]  # header name

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
      <td>James</td>
      <td>32</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jenny</td>
      <td>24</td>
      <td>web designer</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pawl</td>
      <td>45</td>
      <td>it manager</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Export the data frame to csv
# In the same directory, you can see the file is created.
df.to_csv('people.csv')
```

The file created looks like the following :

![image](https://user-images.githubusercontent.com/79891496/110217977-2582a080-7e85-11eb-8f49-087db69de091.png)


How can we remove the first column?

By default, header and index are True like below :
```python
df.to_csv('people.csv', header = True, index = True)
```

- **header = False** means you don't want to create column names. no 0,1,2 at column name
- **index = False** means you don't want to create row names. no 0,1,2 at row name

In this case, you can set up the index as False


```python
df.to_csv('people.csv', index=False)
```

Result : 

![image](https://user-images.githubusercontent.com/79891496/110217997-3fbc7e80-7e85-11eb-8fb7-45fb891ffab8.png)

## How to replace None value to something else?

Sometimes, you face the data including 'None' value.

In this case, you can use __na_rep__ argument in to_csv method.


```python
# Let's take a look at the below example
employees = [
    {'name': 'James', 'age': 32, 'job': 'developer'},
    {'name': 'Jenny', 'age': None, 'job': 'web designer'},
    {'name': 'Pawl', 'age': 45, 'job': None}
]

df = pd.DataFrame(employees)
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
      <td>James</td>
      <td>32.0</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jenny</td>
      <td>NaN</td>
      <td>web designer</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pawl</td>
      <td>45.0</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Use na_rep argument in to_csv() menthod
df.to_csv('employees.csv', index=False, na_rep='-')
```

Result : 

![image](https://user-images.githubusercontent.com/79891496/110218000-51058b00-7e85-11eb-8bc7-7b42d9002530.png)


```python

```
