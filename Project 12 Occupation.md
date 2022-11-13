# Occupation

### Introduction:

Special thanks to: https://github.com/justmarkham for sharing the dataset and materials.

### Step 1. Import the necessary libraries


```python
import pandas as pd 
import numpy as np 
```

### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/justmarkham/DAT8/master/data/u.user). 

### Step 3. Assign it to a variable called users.


```python
df = pd.read_csv("https://raw.githubusercontent.com/justmarkham/DAT8/master/data/u.user", sep="|")
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
      <th>user_id</th>
      <th>age</th>
      <th>gender</th>
      <th>occupation</th>
      <th>zip_code</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>24</td>
      <td>M</td>
      <td>technician</td>
      <td>85711</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>53</td>
      <td>F</td>
      <td>other</td>
      <td>94043</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>23</td>
      <td>M</td>
      <td>writer</td>
      <td>32067</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>24</td>
      <td>M</td>
      <td>technician</td>
      <td>43537</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>33</td>
      <td>F</td>
      <td>other</td>
      <td>15213</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>938</th>
      <td>939</td>
      <td>26</td>
      <td>F</td>
      <td>student</td>
      <td>33319</td>
    </tr>
    <tr>
      <th>939</th>
      <td>940</td>
      <td>32</td>
      <td>M</td>
      <td>administrator</td>
      <td>02215</td>
    </tr>
    <tr>
      <th>940</th>
      <td>941</td>
      <td>20</td>
      <td>M</td>
      <td>student</td>
      <td>97229</td>
    </tr>
    <tr>
      <th>941</th>
      <td>942</td>
      <td>48</td>
      <td>F</td>
      <td>librarian</td>
      <td>78209</td>
    </tr>
    <tr>
      <th>942</th>
      <td>943</td>
      <td>22</td>
      <td>M</td>
      <td>student</td>
      <td>77841</td>
    </tr>
  </tbody>
</table>
<p>943 rows × 5 columns</p>
</div>



### Step 4. Discover what is the mean age per occupation


```python
df.groupby("occupation").age.mean()
```




    occupation
    administrator    38.746835
    artist           31.392857
    doctor           43.571429
    educator         42.010526
    engineer         36.388060
    entertainment    29.222222
    executive        38.718750
    healthcare       41.562500
    homemaker        32.571429
    lawyer           36.750000
    librarian        40.000000
    marketing        37.615385
    none             26.555556
    other            34.523810
    programmer       33.121212
    retired          63.071429
    salesman         35.666667
    scientist        35.548387
    student          22.081633
    technician       33.148148
    writer           36.311111
    Name: age, dtype: float64



### Step 5. Discover the Male ratio per occupation and sort it from the most to the least


```python
df['is_male'] = df.gender.apply(lambda x: True if x == 'M' else False)
df['is_male']
```




    0       True
    1      False
    2       True
    3       True
    4      False
           ...  
    938    False
    939     True
    940     True
    941    False
    942     True
    Name: is_male, Length: 943, dtype: bool



### Step 6. For each occupation, calculate the minimum and maximum ages


```python
df.groupby('occupation').age.agg(['min', 'max'])
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
      <th>min</th>
      <th>max</th>
    </tr>
    <tr>
      <th>occupation</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>administrator</th>
      <td>21</td>
      <td>70</td>
    </tr>
    <tr>
      <th>artist</th>
      <td>19</td>
      <td>48</td>
    </tr>
    <tr>
      <th>doctor</th>
      <td>28</td>
      <td>64</td>
    </tr>
    <tr>
      <th>educator</th>
      <td>23</td>
      <td>63</td>
    </tr>
    <tr>
      <th>engineer</th>
      <td>22</td>
      <td>70</td>
    </tr>
    <tr>
      <th>entertainment</th>
      <td>15</td>
      <td>50</td>
    </tr>
    <tr>
      <th>executive</th>
      <td>22</td>
      <td>69</td>
    </tr>
    <tr>
      <th>healthcare</th>
      <td>22</td>
      <td>62</td>
    </tr>
    <tr>
      <th>homemaker</th>
      <td>20</td>
      <td>50</td>
    </tr>
    <tr>
      <th>lawyer</th>
      <td>21</td>
      <td>53</td>
    </tr>
    <tr>
      <th>librarian</th>
      <td>23</td>
      <td>69</td>
    </tr>
    <tr>
      <th>marketing</th>
      <td>24</td>
      <td>55</td>
    </tr>
    <tr>
      <th>none</th>
      <td>11</td>
      <td>55</td>
    </tr>
    <tr>
      <th>other</th>
      <td>13</td>
      <td>64</td>
    </tr>
    <tr>
      <th>programmer</th>
      <td>20</td>
      <td>63</td>
    </tr>
    <tr>
      <th>retired</th>
      <td>51</td>
      <td>73</td>
    </tr>
    <tr>
      <th>salesman</th>
      <td>18</td>
      <td>66</td>
    </tr>
    <tr>
      <th>scientist</th>
      <td>23</td>
      <td>55</td>
    </tr>
    <tr>
      <th>student</th>
      <td>7</td>
      <td>42</td>
    </tr>
    <tr>
      <th>technician</th>
      <td>21</td>
      <td>55</td>
    </tr>
    <tr>
      <th>writer</th>
      <td>18</td>
      <td>60</td>
    </tr>
  </tbody>
</table>
</div>



### Step 7. For each combination of occupation and gender, calculate the mean age


```python
df.groupby(['occupation', 'gender']).age.mean()
```




    occupation     gender
    administrator  F         40.638889
                   M         37.162791
    artist         F         30.307692
                   M         32.333333
    doctor         M         43.571429
    educator       F         39.115385
                   M         43.101449
    engineer       F         29.500000
                   M         36.600000
    entertainment  F         31.000000
                   M         29.000000
    executive      F         44.000000
                   M         38.172414
    healthcare     F         39.818182
                   M         45.400000
    homemaker      F         34.166667
                   M         23.000000
    lawyer         F         39.500000
                   M         36.200000
    librarian      F         40.000000
                   M         40.000000
    marketing      F         37.200000
                   M         37.875000
    none           F         36.500000
                   M         18.600000
    other          F         35.472222
                   M         34.028986
    programmer     F         32.166667
                   M         33.216667
    retired        F         70.000000
                   M         62.538462
    salesman       F         27.000000
                   M         38.555556
    scientist      F         28.333333
                   M         36.321429
    student        F         20.750000
                   M         22.669118
    technician     F         38.000000
                   M         32.961538
    writer         F         37.631579
                   M         35.346154
    Name: age, dtype: float64



### Step 8.  For each occupation present the percentage of women and men


```python
occup_count = df.groupby(['occupation']).count()
occup_count
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
      <th>user_id</th>
      <th>age</th>
      <th>gender</th>
      <th>zip_code</th>
      <th>is_male</th>
    </tr>
    <tr>
      <th>occupation</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>administrator</th>
      <td>79</td>
      <td>79</td>
      <td>79</td>
      <td>79</td>
      <td>79</td>
    </tr>
    <tr>
      <th>artist</th>
      <td>28</td>
      <td>28</td>
      <td>28</td>
      <td>28</td>
      <td>28</td>
    </tr>
    <tr>
      <th>doctor</th>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
    </tr>
    <tr>
      <th>educator</th>
      <td>95</td>
      <td>95</td>
      <td>95</td>
      <td>95</td>
      <td>95</td>
    </tr>
    <tr>
      <th>engineer</th>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
      <td>67</td>
    </tr>
    <tr>
      <th>entertainment</th>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
    </tr>
    <tr>
      <th>executive</th>
      <td>32</td>
      <td>32</td>
      <td>32</td>
      <td>32</td>
      <td>32</td>
    </tr>
    <tr>
      <th>healthcare</th>
      <td>16</td>
      <td>16</td>
      <td>16</td>
      <td>16</td>
      <td>16</td>
    </tr>
    <tr>
      <th>homemaker</th>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
    </tr>
    <tr>
      <th>lawyer</th>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
    </tr>
    <tr>
      <th>librarian</th>
      <td>51</td>
      <td>51</td>
      <td>51</td>
      <td>51</td>
      <td>51</td>
    </tr>
    <tr>
      <th>marketing</th>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
    </tr>
    <tr>
      <th>none</th>
      <td>9</td>
      <td>9</td>
      <td>9</td>
      <td>9</td>
      <td>9</td>
    </tr>
    <tr>
      <th>other</th>
      <td>105</td>
      <td>105</td>
      <td>105</td>
      <td>105</td>
      <td>105</td>
    </tr>
    <tr>
      <th>programmer</th>
      <td>66</td>
      <td>66</td>
      <td>66</td>
      <td>66</td>
      <td>66</td>
    </tr>
    <tr>
      <th>retired</th>
      <td>14</td>
      <td>14</td>
      <td>14</td>
      <td>14</td>
      <td>14</td>
    </tr>
    <tr>
      <th>salesman</th>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
    </tr>
    <tr>
      <th>scientist</th>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
    </tr>
    <tr>
      <th>student</th>
      <td>196</td>
      <td>196</td>
      <td>196</td>
      <td>196</td>
      <td>196</td>
    </tr>
    <tr>
      <th>technician</th>
      <td>27</td>
      <td>27</td>
      <td>27</td>
      <td>27</td>
      <td>27</td>
    </tr>
    <tr>
      <th>writer</th>
      <td>45</td>
      <td>45</td>
      <td>45</td>
      <td>45</td>
      <td>45</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.describe(include="all")
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
      <th>user_id</th>
      <th>age</th>
      <th>gender</th>
      <th>occupation</th>
      <th>zip_code</th>
      <th>is_male</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>943.000000</td>
      <td>943.000000</td>
      <td>943</td>
      <td>943</td>
      <td>943</td>
      <td>943</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>2</td>
      <td>21</td>
      <td>795</td>
      <td>2</td>
    </tr>
    <tr>
      <th>top</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>M</td>
      <td>student</td>
      <td>55414</td>
      <td>True</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>670</td>
      <td>196</td>
      <td>9</td>
      <td>670</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>472.000000</td>
      <td>34.051962</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>std</th>
      <td>272.364951</td>
      <td>12.192740</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>7.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>236.500000</td>
      <td>25.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>472.000000</td>
      <td>31.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>707.500000</td>
      <td>43.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>max</th>
      <td>943.000000</td>
      <td>73.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>


