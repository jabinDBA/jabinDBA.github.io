# What is Pandas?

- An open source Python package
- It offers data structures and operations for manipulating numerical tables and time series

# Data Structure

Pandas deals with the following three data structures
- Series
- Data Frame
- Pannel

Simply think as follows:
- Series is 1-dimentional labeled
- Data Frame is 2-dimentional labeled
- Pannel is 3-dimentional labeled

# Data Frame

- A 2-dimensional labeled data structure
- Comes with columns of potentially different types
- Like a spreadsheet or SQL table


```python
# import pandas and we call this as 'pd''
# If you see ModuleNotFoundError, then should go to cmd and type 'pip install pandas'
import pandas as pd
```


```python
# Let's create a dataframe based on .csv installed in data dir
data_frame = pd.read_csv('data/friend_list.csv')
```


```python
data_frame
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
      <td>developer</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Nate</td>
      <td>30</td>
      <td>teacher</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Julia</td>
      <td>40</td>
      <td>dentist</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Brian</td>
      <td>45</td>
      <td>manager</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Chris</td>
      <td>25</td>
      <td>intern</td>
    </tr>
  </tbody>
</table>
</div>




```python
# View the top 2 rows of the frame
data_frame.head(2)
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
      <td>developer</td>
    </tr>
  </tbody>
</table>
</div>




```python
# View the bottom 2 rows of the frame
data_frame.tail(2)
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
      <th>4</th>
      <td>Brian</td>
      <td>45</td>
      <td>manager</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Chris</td>
      <td>25</td>
      <td>intern</td>
    </tr>
  </tbody>
</table>
</div>



# Series

- A 1-dimentional labeled array
- Simply can say that data frame is a collection of series


```python
type(data_frame.job)
```




    pandas.core.series.Series




```python
# Let's create series and then data frame
s1 = pd.core.series.Series([1,2,3])
s2 = pd.core.series.Series(['one', 'two', 'three'])

pd.DataFrame(data=dict(num=s1, word=s2))
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
      <th>num</th>
      <th>word</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>one</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>two</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>three</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
