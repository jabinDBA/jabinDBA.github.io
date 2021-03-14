# Adding new column to existing DataFrame

## By declaring a new list as a column

Let's take a look at the sample data below


```python
# Create a data frame by dictionary

import pandas as pd

employee_list = [
    {'name': 'John', 'age': 25, 'job': 'developer'},
    {'name': 'Smith', 'age': 35, 'job': 'web designer'},
    {'name': 'Nate', 'age': 23, 'job': 'data analyst'},
    {'name': 'Mathew', 'age': 46, 'job': 'project manager'},
    {'name': 'Jason', 'age': 30, 'job': 'data scientist'},
]

df = pd.DataFrame(employee_list)
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
      <td>25</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Smith</td>
      <td>35</td>
      <td>web designer</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nate</td>
      <td>23</td>
      <td>data analyst</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mathew</td>
      <td>46</td>
      <td>project manager</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jason</td>
      <td>30</td>
      <td>data scientist</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Add a new column called 'salary'

df['salary'] = 0
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
      <th>salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>25</td>
      <td>developer</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Smith</td>
      <td>35</td>
      <td>web designer</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nate</td>
      <td>23</td>
      <td>data analyst</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mathew</td>
      <td>46</td>
      <td>project manager</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jason</td>
      <td>30</td>
      <td>data scientist</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



Let's say another example : 


```python
friends_list = [
    {'name': 'John', 'age': 25, 'job': 'developer'},
    {'name': 'Smith', 'age': 35, 'job': 'web designer'},
    {'name': 'Nate', 'age': 23, 'job': 'data analyst'},
    {'name': 'Denny', 'age': 23, 'job': 'student'},
    {'name': 'Mathew', 'age': 46, 'job': 'project manager'},
    {'name': 'Jason', 'age': 30, 'job': 'data scientist'},
    {'name': 'Edward', 'age': 28, 'job': 'unemployeed'}
]

df = pd.DataFrame(friends_list)
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
      <td>25</td>
      <td>developer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Smith</td>
      <td>35</td>
      <td>web designer</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nate</td>
      <td>23</td>
      <td>data analyst</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Denny</td>
      <td>23</td>
      <td>student</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Mathew</td>
      <td>46</td>
      <td>project manager</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Jason</td>
      <td>30</td>
      <td>data scientist</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Edward</td>
      <td>28</td>
      <td>unemployeed</td>
    </tr>
  </tbody>
</table>
</div>




```python
# One liner adding column by true or false condition

# np.where(condition[, x, y])
# If both x and y are specified, the output array contains elements of x where condition is True, and elements from y elsewhere.
# More Details : https://www.geeksforgeeks.org/numpy-where-in-python/

import numpy as np

df['salary'] = np.where((df['job'] == 'student') | (df['job'] == 'unemployeed'), 'no', 'yes')
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
      <th>salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>25</td>
      <td>developer</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Smith</td>
      <td>35</td>
      <td>web designer</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nate</td>
      <td>23</td>
      <td>data analyst</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Denny</td>
      <td>23</td>
      <td>student</td>
      <td>no</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Mathew</td>
      <td>46</td>
      <td>project manager</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Jason</td>
      <td>30</td>
      <td>data scientist</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Edward</td>
      <td>28</td>
      <td>unemployeed</td>
      <td>no</td>
    </tr>
  </tbody>
</table>
</div>



## column derived from adding two existing columns

Here is another example


```python
student_list = [
    {'name': 'John', 'midterm': 67, 'final': 89},
    {'name': 'Smith', 'midterm': 43, 'final': 90},
    {'name': 'Jenny', 'midterm': 89, 'final': 88},
    {'name': 'Binz', 'midterm': 90, 'final': 58},
    {'name': 'Mcnoald', 'midterm': 34, 'final': 99}
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
      <th>midterm</th>
      <th>final</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>67</td>
      <td>89</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Smith</td>
      <td>43</td>
      <td>90</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jenny</td>
      <td>89</td>
      <td>88</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Binz</td>
      <td>90</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Mcnoald</td>
      <td>34</td>
      <td>99</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Total = Minterm + Final

df['total'] = df['midterm'] + df['final']
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
      <th>midterm</th>
      <th>final</th>
      <th>total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>67</td>
      <td>89</td>
      <td>156</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Smith</td>
      <td>43</td>
      <td>90</td>
      <td>133</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jenny</td>
      <td>89</td>
      <td>88</td>
      <td>177</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Binz</td>
      <td>90</td>
      <td>58</td>
      <td>148</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Mcnoald</td>
      <td>34</td>
      <td>99</td>
      <td>133</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Average = (midterm + final) / 2

df['average'] = df['total'] / 2
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
      <th>midterm</th>
      <th>final</th>
      <th>total</th>
      <th>average</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>67</td>
      <td>89</td>
      <td>156</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Smith</td>
      <td>43</td>
      <td>90</td>
      <td>133</td>
      <td>66.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jenny</td>
      <td>89</td>
      <td>88</td>
      <td>177</td>
      <td>88.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Binz</td>
      <td>90</td>
      <td>58</td>
      <td>148</td>
      <td>74.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Mcnoald</td>
      <td>34</td>
      <td>99</td>
      <td>133</td>
      <td>66.5</td>
    </tr>
  </tbody>
</table>
</div>



## Add column by condition

Let's classify students by grade (A to F)


```python
# Create a empty list called 'grades'

grades = []
```


```python
# Depedning on the average, we will classify the data by grade (A to F)

for row in df['average']:
    if row >= 90:
        grades.append('A')
    elif row >= 80:
        grades.append('B')
    elif row >= 70:
        grades.append('C')
    else:
        grades.append('F')
```


```python
# Create a new column called 'grade' and insert the data we just created into the column

df['grade'] = grades
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
      <th>midterm</th>
      <th>final</th>
      <th>total</th>
      <th>average</th>
      <th>grade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>67</td>
      <td>89</td>
      <td>156</td>
      <td>78.0</td>
      <td>C</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Smith</td>
      <td>43</td>
      <td>90</td>
      <td>133</td>
      <td>66.5</td>
      <td>F</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jenny</td>
      <td>89</td>
      <td>88</td>
      <td>177</td>
      <td>88.5</td>
      <td>B</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Binz</td>
      <td>90</td>
      <td>58</td>
      <td>148</td>
      <td>74.0</td>
      <td>C</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Mcnoald</td>
      <td>34</td>
      <td>99</td>
      <td>133</td>
      <td>66.5</td>
      <td>F</td>
    </tr>
  </tbody>
</table>
</div>



## Apply a function to DataFrame

Use pandas.DataFrame.apply(func)

See Details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.apply.html


```python
# Create a function

def pass_or_false(row):
    print(row)
    if row != 'F':
        return 'Pass'
    else:
        return 'Fail'
```


```python
# Use pandas.DataFrame.apply(func)

df.grade = df.grade.apply(pass_or_false)
```

    C
    F
    B
    C
    F
    


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
      <th>midterm</th>
      <th>final</th>
      <th>total</th>
      <th>average</th>
      <th>grade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>67</td>
      <td>89</td>
      <td>156</td>
      <td>78.0</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Smith</td>
      <td>43</td>
      <td>90</td>
      <td>133</td>
      <td>66.5</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jenny</td>
      <td>89</td>
      <td>88</td>
      <td>177</td>
      <td>88.5</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Binz</td>
      <td>90</td>
      <td>58</td>
      <td>148</td>
      <td>74.0</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Mcnoald</td>
      <td>34</td>
      <td>99</td>
      <td>133</td>
      <td>66.5</td>
      <td>Fail</td>
    </tr>
  </tbody>
</table>
</div>



## Extract necessary data through pandas.DataFrame.apply()

Let's say we have the data formated 'yyyy-mm-dd' as follows:


```python
date_list = [
    {'yyyy-mm-dd': '2020-03-13'},
    {'yyyy-mm-dd': '2019-05-31'},
    {'yyyy-mm-dd': '2010-10-25'},
]

df = pd.DataFrame(date_list)
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
      <th>yyyy-mm-dd</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2020-03-13</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019-05-31</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2010-10-25</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create a function that separates dates based on '-'

def seperator_year(row):
    return row.split('-')[0]
```


```python
# Use pandas.DataFrame.apply(func)

df['year'] = df['yyyy-mm-dd'].apply(seperator_year)
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
      <th>yyyy-mm-dd</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2020-03-13</td>
      <td>2020</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2019-05-31</td>
      <td>2019</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2010-10-25</td>
      <td>2010</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
