# Group by

We are going to group data and compute operations on these groups such as counting the number of rows in this chapter.


## What is pandas.DataFrame.groupby()?
- This is used to group DataFrame using a mapper or by a Series of columns.
- A groupby operation involves some combination of splitting the object, applying a function, and combining the results.

See More Details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.groupby.html


Let's take a look the following example :


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
    {'name': 'Sera', 'major': "Psychology", 'sex': "female"}
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
  </tbody>
</table>
</div>



How to group the data by __major__?


```python
df_groupby = df.groupby('major')
```


```python
df_groupby.groups
```




    {'Computer Science': [0, 1, 6, 7], 'Economics': [4, 5, 9], 'Physics': [2], 'Psychology': [3, 8, 10]}




```python
for name, group in df_groupby:
    print(name + ' : ' + str(len(group)))
    print(group)
    print()
```

    Computer Science : 4
           name             major     sex
    0      John  Computer Science    male
    1      Nate  Computer Science    male
    6  Jeniffer  Computer Science  female
    7    Edward  Computer Science    male
    
    Economics : 3
        name      major     sex
    4  Janny  Economics  female
    5   Yuna  Economics  female
    9  Wendy  Economics  female
    
    Physics : 1
          name    major   sex
    2  Abraham  Physics  male
    
    Psychology : 3
         name       major     sex
    3   Brian  Psychology    male
    8    Zara  Psychology  female
    10   Sera  Psychology  female
    
    

How to __count__ the number of rows by the group?

- Answer : Use pandas.DataFrame.size()
- Returns the number of rows if Series. Otherwise return the number of rows times number of columns if DataFrame.
- See Details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.size.html


```python
df_groupby_major = df.groupby('major')

df_counted_by_major = pd.DataFrame({
    'count': df_groupby_major.size()
})
```


```python
df_counted_by_major
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
      <th>count</th>
    </tr>
    <tr>
      <th>major</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Computer Science</th>
      <td>4</td>
    </tr>
    <tr>
      <th>Economics</th>
      <td>3</td>
    </tr>
    <tr>
      <th>Physics</th>
      <td>1</td>
    </tr>
    <tr>
      <th>Psychology</th>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



If you want to remove the header, major',

- Use pandas.DataFrame.reset_index().
- Reset the index, or a level of it.
- See more details : https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.reset_index.html


```python
df_counted_by_major = pd.DataFrame({
    'count' : df.groupby('major').size()
}).reset_index()
```


```python
df_counted_by_major
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
      <th>major</th>
      <th>count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Computer Science</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Economics</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Physics</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Psychology</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



Let's group the data by sex this time.


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




```python
df_groupby_sex = df.groupby('sex')
```


```python
for name, group in df_groupby_sex:
    print(name + ' : ' + str(len(group)))
    print(group)
    print()
```

    female : 6
            name             major     sex
    4      Janny         Economics  female
    5       Yuna         Economics  female
    6   Jeniffer  Computer Science  female
    8       Zara        Psychology  female
    9      Wendy         Economics  female
    10      Sera        Psychology  female
    
    male : 5
          name             major   sex
    0     John  Computer Science  male
    1     Nate  Computer Science  male
    2  Abraham           Physics  male
    3    Brian        Psychology  male
    7   Edward  Computer Science  male
    
    

Let's count the number of rows by sex


```python
df_counted_sex = pd.DataFrame({
    'count' : df.groupby('sex').size()
}).reset_index()
```


```python
df_counted_sex
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
      <th>sex</th>
      <th>count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>female</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>male</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
