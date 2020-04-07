# Introduction
* From reading datasets to dealing with missing values.


```python
# Importing Pandas library:

import pandas as pd
```


```python
# Reading a .csv database. We'll be using one year of house sales data from a US county.
# *sep* refers to separator, *header* to column headers position.
# If *header* is not defined, numbers will be assigned automatically.

file = 'kc_house_data.csv'
dataset = pd.read_csv(file, sep=',' ,header=0)
```


```python
# Finding out the type of the dataset.
# In a *dataframe*, lines can have columns with different types of data, like strings, integers, etc.

type(dataset)
```




    pandas.core.frame.DataFrame




```python
# *head()* prints the first lines of the dataset, 5 by default.

dataset.head()
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
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>...</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>20141013T000000</td>
      <td>221900.0</td>
      <td>3.0</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1180</td>
      <td>0</td>
      <td>1955</td>
      <td>0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>20141209T000000</td>
      <td>538000.0</td>
      <td>3.0</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>2170</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5631500400</td>
      <td>20150225T000000</td>
      <td>180000.0</td>
      <td>2.0</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6</td>
      <td>770</td>
      <td>0</td>
      <td>1933</td>
      <td>0</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2487200875</td>
      <td>20141209T000000</td>
      <td>604000.0</td>
      <td>4.0</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1050</td>
      <td>910</td>
      <td>1965</td>
      <td>0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>20150218T000000</td>
      <td>510000.0</td>
      <td>3.0</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1680</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>




```python
# *tail()* does the same for the last lines, also 5 by default.

dataset.tail()
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
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>...</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>21608</th>
      <td>263000018</td>
      <td>20140521T000000</td>
      <td>360000.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>1530</td>
      <td>1131</td>
      <td>3.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1530</td>
      <td>0</td>
      <td>2009</td>
      <td>0</td>
      <td>98103</td>
      <td>47.6993</td>
      <td>-122.346</td>
      <td>1530</td>
      <td>1509</td>
    </tr>
    <tr>
      <th>21609</th>
      <td>6600060120</td>
      <td>20150223T000000</td>
      <td>400000.0</td>
      <td>4.0</td>
      <td>2.50</td>
      <td>2310</td>
      <td>5813</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>2310</td>
      <td>0</td>
      <td>2014</td>
      <td>0</td>
      <td>98146</td>
      <td>47.5107</td>
      <td>-122.362</td>
      <td>1830</td>
      <td>7200</td>
    </tr>
    <tr>
      <th>21610</th>
      <td>1523300141</td>
      <td>20140623T000000</td>
      <td>402101.0</td>
      <td>2.0</td>
      <td>0.75</td>
      <td>1020</td>
      <td>1350</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1020</td>
      <td>0</td>
      <td>2009</td>
      <td>0</td>
      <td>98144</td>
      <td>47.5944</td>
      <td>-122.299</td>
      <td>1020</td>
      <td>2007</td>
    </tr>
    <tr>
      <th>21611</th>
      <td>291310100</td>
      <td>20150116T000000</td>
      <td>400000.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>1600</td>
      <td>2388</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1600</td>
      <td>0</td>
      <td>2004</td>
      <td>0</td>
      <td>98027</td>
      <td>47.5345</td>
      <td>-122.069</td>
      <td>1410</td>
      <td>1287</td>
    </tr>
    <tr>
      <th>21612</th>
      <td>1523300157</td>
      <td>20141015T000000</td>
      <td>325000.0</td>
      <td>2.0</td>
      <td>0.75</td>
      <td>1020</td>
      <td>1076</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1020</td>
      <td>0</td>
      <td>2008</td>
      <td>0</td>
      <td>98144</td>
      <td>47.5941</td>
      <td>-122.299</td>
      <td>1020</td>
      <td>1357</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>




```python
# *sample()* gives us a randomized sample from the dataset, just 1 by default.

dataset.sample()
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
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>...</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9132</th>
      <td>1471700410</td>
      <td>20150506T000000</td>
      <td>310000.0</td>
      <td>7.0</td>
      <td>1.5</td>
      <td>2660</td>
      <td>15111</td>
      <td>1.5</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>2660</td>
      <td>0</td>
      <td>1962</td>
      <td>0</td>
      <td>98059</td>
      <td>47.4644</td>
      <td>-122.066</td>
      <td>1710</td>
      <td>15429</td>
    </tr>
  </tbody>
</table>
<p>1 rows × 21 columns</p>
</div>




```python
# *count()* returns the number of lines below all columns:

dataset.count()
```




    id               21613
    date             21613
    price            21613
    bedrooms         21609
    bathrooms        21613
    sqft_living      21613
    sqft_lot         21613
    floors           21612
    waterfront       21613
    view             21613
    condition        21613
    grade            21613
    sqft_above       21613
    sqft_basement    21613
    yr_built         21613
    yr_renovated     21613
    zipcode          21613
    lat              21613
    long             21613
    sqft_living15    21613
    sqft_lot15       21613
    dtype: int64




```python
# *Columns* attribute returns names of column headers:

dataset.columns
```




    Index(['id', 'date', 'price', 'bedrooms', 'bathrooms', 'sqft_living',
           'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
           'sqft_above', 'sqft_basement', 'yr_built', 'yr_renovated', 'zipcode',
           'lat', 'long', 'sqft_living15', 'sqft_lot15'],
          dtype='object')




```python
# *describe()* prints statistical information about the database:

dataset.describe()
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
      <th>id</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>2.161300e+04</td>
      <td>2.161300e+04</td>
      <td>21609.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>2.161300e+04</td>
      <td>21612.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
      <td>21613.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>4.580302e+09</td>
      <td>5.400881e+05</td>
      <td>3.370910</td>
      <td>2.114757</td>
      <td>2079.899736</td>
      <td>1.510697e+04</td>
      <td>1.494332</td>
      <td>0.007542</td>
      <td>0.234303</td>
      <td>3.409430</td>
      <td>7.656873</td>
      <td>1788.390691</td>
      <td>291.509045</td>
      <td>1971.005136</td>
      <td>84.402258</td>
      <td>98077.939805</td>
      <td>47.560053</td>
      <td>-122.213896</td>
      <td>1986.552492</td>
      <td>12768.455652</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2.876566e+09</td>
      <td>3.671272e+05</td>
      <td>0.930084</td>
      <td>0.770163</td>
      <td>918.440897</td>
      <td>4.142051e+04</td>
      <td>0.539991</td>
      <td>0.086517</td>
      <td>0.766318</td>
      <td>0.650743</td>
      <td>1.175459</td>
      <td>828.090978</td>
      <td>442.575043</td>
      <td>29.373411</td>
      <td>401.679240</td>
      <td>53.505026</td>
      <td>0.138564</td>
      <td>0.140828</td>
      <td>685.391304</td>
      <td>27304.179631</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000102e+06</td>
      <td>7.500000e+04</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>290.000000</td>
      <td>5.200000e+02</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>290.000000</td>
      <td>0.000000</td>
      <td>1900.000000</td>
      <td>0.000000</td>
      <td>98001.000000</td>
      <td>47.155900</td>
      <td>-122.519000</td>
      <td>399.000000</td>
      <td>651.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2.123049e+09</td>
      <td>3.219500e+05</td>
      <td>3.000000</td>
      <td>1.750000</td>
      <td>1427.000000</td>
      <td>5.040000e+03</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>3.000000</td>
      <td>7.000000</td>
      <td>1190.000000</td>
      <td>0.000000</td>
      <td>1951.000000</td>
      <td>0.000000</td>
      <td>98033.000000</td>
      <td>47.471000</td>
      <td>-122.328000</td>
      <td>1490.000000</td>
      <td>5100.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>3.904930e+09</td>
      <td>4.500000e+05</td>
      <td>3.000000</td>
      <td>2.250000</td>
      <td>1910.000000</td>
      <td>7.618000e+03</td>
      <td>1.500000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>3.000000</td>
      <td>7.000000</td>
      <td>1560.000000</td>
      <td>0.000000</td>
      <td>1975.000000</td>
      <td>0.000000</td>
      <td>98065.000000</td>
      <td>47.571800</td>
      <td>-122.230000</td>
      <td>1840.000000</td>
      <td>7620.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>7.308900e+09</td>
      <td>6.450000e+05</td>
      <td>4.000000</td>
      <td>2.500000</td>
      <td>2550.000000</td>
      <td>1.068800e+04</td>
      <td>2.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>4.000000</td>
      <td>8.000000</td>
      <td>2210.000000</td>
      <td>560.000000</td>
      <td>1997.000000</td>
      <td>0.000000</td>
      <td>98118.000000</td>
      <td>47.678000</td>
      <td>-122.125000</td>
      <td>2360.000000</td>
      <td>10083.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>9.900000e+09</td>
      <td>7.700000e+06</td>
      <td>33.000000</td>
      <td>8.000000</td>
      <td>13540.000000</td>
      <td>1.651359e+06</td>
      <td>3.500000</td>
      <td>1.000000</td>
      <td>4.000000</td>
      <td>5.000000</td>
      <td>13.000000</td>
      <td>9410.000000</td>
      <td>4820.000000</td>
      <td>2015.000000</td>
      <td>2015.000000</td>
      <td>98199.000000</td>
      <td>47.777600</td>
      <td>-121.315000</td>
      <td>6210.000000</td>
      <td>871200.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# *Shape* attribute returns number of dataset lines and columns in tuple format:

dataset.shape
```




    (21613, 21)




```python
# *info()* returns information about columns and memory use:

dataset.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 21613 entries, 0 to 21612
    Data columns (total 21 columns):
     #   Column         Non-Null Count  Dtype  
    ---  ------         --------------  -----  
     0   id             21613 non-null  int64  
     1   date           21613 non-null  object 
     2   price          21613 non-null  float64
     3   bedrooms       21609 non-null  float64
     4   bathrooms      21613 non-null  float64
     5   sqft_living    21613 non-null  int64  
     6   sqft_lot       21613 non-null  int64  
     7   floors         21612 non-null  float64
     8   waterfront     21613 non-null  int64  
     9   view           21613 non-null  int64  
     10  condition      21613 non-null  int64  
     11  grade          21613 non-null  int64  
     12  sqft_above     21613 non-null  int64  
     13  sqft_basement  21613 non-null  int64  
     14  yr_built       21613 non-null  int64  
     15  yr_renovated   21613 non-null  int64  
     16  zipcode        21613 non-null  int64  
     17  lat            21613 non-null  float64
     18  long           21613 non-null  float64
     19  sqft_living15  21613 non-null  int64  
     20  sqft_lot15     21613 non-null  int64  
    dtypes: float64(6), int64(14), object(1)
    memory usage: 3.5+ MB
    


```python
# It's important to manage memory use with large files.
# One way to do so is by reading a limited portion of the dataset at a time.
# We can split the data into *chunks* for this purpose.
# *chunksize()* parameter defines number of lines per chunk.

chunk = pd.read_csv(file, chunksize=10000)
```


```python
type(chunk)
```




    pandas.io.parsers.TextFileReader




```python
# Checking chunk size using length method:

for part in chunk:
    print (len(part))
```

    10000
    10000
    1613
    


```python
# Working with correct data types also helps with memory use.
# Let's work with a different database for this example, the Titanic passenger manifest.

manifest = pd.read_csv("titanic.csv")
```


```python
manifest.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 891 entries, 0 to 890
    Data columns (total 12 columns):
     #   Column       Non-Null Count  Dtype  
    ---  ------       --------------  -----  
     0   PassengerId  891 non-null    int64  
     1   Survived     891 non-null    int64  
     2   Pclass       891 non-null    int64  
     3   Name         891 non-null    object 
     4   Sex          891 non-null    object 
     5   Age          714 non-null    float64
     6   SibSp        891 non-null    int64  
     7   Parch        891 non-null    int64  
     8   Ticket       891 non-null    object 
     9   Fare         891 non-null    float64
     10  Cabin        204 non-null    object 
     11  Embarked     889 non-null    object 
    dtypes: float64(2), int64(5), object(5)
    memory usage: 83.7+ KB
    


```python
# Special attention to *object* types (strings in "vanilla" Python).
# Certain *objects* can be altered to *categories* (finite lists) for memory optimization.
# 64-bit integers can also be changed to 32-bit for better memory use.

manifest.Sex = manifest.Sex.astype('category')
manifest.Embarked = manifest.Embarked.astype('category')
manifest.Survived = manifest.Survived.astype('category')
manifest.Pclass = manifest.Pclass.astype('category')
manifest.PassengerId = manifest.PassengerId.astype('int32')
manifest.Parch = manifest.Parch.astype('int32')
manifest.SibSp = manifest.SibSp.astype('int32')
```


```python
manifest.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 891 entries, 0 to 890
    Data columns (total 12 columns):
     #   Column       Non-Null Count  Dtype   
    ---  ------       --------------  -----   
     0   PassengerId  891 non-null    int32   
     1   Survived     891 non-null    category
     2   Pclass       891 non-null    category
     3   Name         891 non-null    object  
     4   Sex          891 non-null    category
     5   Age          714 non-null    float64 
     6   SibSp        891 non-null    int32   
     7   Parch        891 non-null    int32   
     8   Ticket       891 non-null    object  
     9   Fare         891 non-null    float64 
     10  Cabin        204 non-null    object  
     11  Embarked     889 non-null    category
    dtypes: category(4), float64(2), int32(3), object(3)
    memory usage: 49.2+ KB
    


```python
# Almost 50% less memory use! (83.7+ KB to 49.2+ KB)
```


```python
# We can run all types of queries on data using logical operators, much like in SQL.
# Let's do some examples. Going back to the house sales data, how many unique values are there for bedrooms?

pd.value_counts(dataset['bedrooms'])
```




    3.0     9822
    4.0     6881
    2.0     2759
    5.0     1601
    6.0      272
    1.0      199
    7.0       38
    8.0       13
    0.0       13
    9.0        6
    10.0       3
    11.0       1
    33.0       1
    Name: bedrooms, dtype: int64




```python
# *loc()* accesses a group of rows/columns using a parameter (label, list/array of labels or boolean array)
# Query for 3-bedroom houses:

dataset.loc[dataset['bedrooms'] == 3]
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
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>...</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>20141013T000000</td>
      <td>221900.0</td>
      <td>3.0</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1180</td>
      <td>0</td>
      <td>1955</td>
      <td>0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>20141209T000000</td>
      <td>538000.0</td>
      <td>3.0</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>2170</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>20150218T000000</td>
      <td>510000.0</td>
      <td>3.0</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1680</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1321400060</td>
      <td>20140627T000000</td>
      <td>257500.0</td>
      <td>3.0</td>
      <td>2.25</td>
      <td>1715</td>
      <td>6819</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1715</td>
      <td>0</td>
      <td>1995</td>
      <td>0</td>
      <td>98003</td>
      <td>47.3097</td>
      <td>-122.327</td>
      <td>2238</td>
      <td>6819</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2008000270</td>
      <td>20150115T000000</td>
      <td>291850.0</td>
      <td>3.0</td>
      <td>1.50</td>
      <td>1060</td>
      <td>9711</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1060</td>
      <td>0</td>
      <td>1963</td>
      <td>0</td>
      <td>98198</td>
      <td>47.4095</td>
      <td>-122.315</td>
      <td>1650</td>
      <td>9711</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>21603</th>
      <td>7852140040</td>
      <td>20140825T000000</td>
      <td>507250.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>2270</td>
      <td>5536</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>2270</td>
      <td>0</td>
      <td>2003</td>
      <td>0</td>
      <td>98065</td>
      <td>47.5389</td>
      <td>-121.881</td>
      <td>2270</td>
      <td>5731</td>
    </tr>
    <tr>
      <th>21604</th>
      <td>9834201367</td>
      <td>20150126T000000</td>
      <td>429000.0</td>
      <td>3.0</td>
      <td>2.00</td>
      <td>1490</td>
      <td>1126</td>
      <td>3.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1490</td>
      <td>0</td>
      <td>2014</td>
      <td>0</td>
      <td>98144</td>
      <td>47.5699</td>
      <td>-122.288</td>
      <td>1400</td>
      <td>1230</td>
    </tr>
    <tr>
      <th>21607</th>
      <td>2997800021</td>
      <td>20150219T000000</td>
      <td>475000.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>1310</td>
      <td>1294</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1180</td>
      <td>130</td>
      <td>2008</td>
      <td>0</td>
      <td>98116</td>
      <td>47.5773</td>
      <td>-122.409</td>
      <td>1330</td>
      <td>1265</td>
    </tr>
    <tr>
      <th>21608</th>
      <td>263000018</td>
      <td>20140521T000000</td>
      <td>360000.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>1530</td>
      <td>1131</td>
      <td>3.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1530</td>
      <td>0</td>
      <td>2009</td>
      <td>0</td>
      <td>98103</td>
      <td>47.6993</td>
      <td>-122.346</td>
      <td>1530</td>
      <td>1509</td>
    </tr>
    <tr>
      <th>21611</th>
      <td>291310100</td>
      <td>20150116T000000</td>
      <td>400000.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>1600</td>
      <td>2388</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1600</td>
      <td>0</td>
      <td>2004</td>
      <td>0</td>
      <td>98027</td>
      <td>47.5345</td>
      <td>-122.069</td>
      <td>1410</td>
      <td>1287</td>
    </tr>
  </tbody>
</table>
<p>9822 rows × 21 columns</p>
</div>




```python
# We can use "&" operator to combine parameters.
# Query for 3-bedroom houses with 2 or more bathrooms:

dataset.loc[(dataset['bedrooms']==3) & (dataset['bathrooms'] >= 2)]
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
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>...</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>20141209T000000</td>
      <td>538000.0</td>
      <td>3.0</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>2170</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>20150218T000000</td>
      <td>510000.0</td>
      <td>3.0</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1680</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1321400060</td>
      <td>20140627T000000</td>
      <td>257500.0</td>
      <td>3.0</td>
      <td>2.25</td>
      <td>1715</td>
      <td>6819</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1715</td>
      <td>0</td>
      <td>1995</td>
      <td>0</td>
      <td>98003</td>
      <td>47.3097</td>
      <td>-122.327</td>
      <td>2238</td>
      <td>6819</td>
    </tr>
    <tr>
      <th>9</th>
      <td>3793500160</td>
      <td>20150312T000000</td>
      <td>323000.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>1890</td>
      <td>6560</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1890</td>
      <td>0</td>
      <td>2003</td>
      <td>0</td>
      <td>98038</td>
      <td>47.3684</td>
      <td>-122.031</td>
      <td>2390</td>
      <td>7570</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1736800520</td>
      <td>20150403T000000</td>
      <td>662500.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>3560</td>
      <td>9796</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1860</td>
      <td>1700</td>
      <td>1965</td>
      <td>0</td>
      <td>98007</td>
      <td>47.6007</td>
      <td>-122.145</td>
      <td>2210</td>
      <td>8925</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>21603</th>
      <td>7852140040</td>
      <td>20140825T000000</td>
      <td>507250.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>2270</td>
      <td>5536</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>2270</td>
      <td>0</td>
      <td>2003</td>
      <td>0</td>
      <td>98065</td>
      <td>47.5389</td>
      <td>-121.881</td>
      <td>2270</td>
      <td>5731</td>
    </tr>
    <tr>
      <th>21604</th>
      <td>9834201367</td>
      <td>20150126T000000</td>
      <td>429000.0</td>
      <td>3.0</td>
      <td>2.00</td>
      <td>1490</td>
      <td>1126</td>
      <td>3.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1490</td>
      <td>0</td>
      <td>2014</td>
      <td>0</td>
      <td>98144</td>
      <td>47.5699</td>
      <td>-122.288</td>
      <td>1400</td>
      <td>1230</td>
    </tr>
    <tr>
      <th>21607</th>
      <td>2997800021</td>
      <td>20150219T000000</td>
      <td>475000.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>1310</td>
      <td>1294</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1180</td>
      <td>130</td>
      <td>2008</td>
      <td>0</td>
      <td>98116</td>
      <td>47.5773</td>
      <td>-122.409</td>
      <td>1330</td>
      <td>1265</td>
    </tr>
    <tr>
      <th>21608</th>
      <td>263000018</td>
      <td>20140521T000000</td>
      <td>360000.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>1530</td>
      <td>1131</td>
      <td>3.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1530</td>
      <td>0</td>
      <td>2009</td>
      <td>0</td>
      <td>98103</td>
      <td>47.6993</td>
      <td>-122.346</td>
      <td>1530</td>
      <td>1509</td>
    </tr>
    <tr>
      <th>21611</th>
      <td>291310100</td>
      <td>20150116T000000</td>
      <td>400000.0</td>
      <td>3.0</td>
      <td>2.50</td>
      <td>1600</td>
      <td>2388</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1600</td>
      <td>0</td>
      <td>2004</td>
      <td>0</td>
      <td>98027</td>
      <td>47.5345</td>
      <td>-122.069</td>
      <td>1410</td>
      <td>1287</td>
    </tr>
  </tbody>
</table>
<p>5324 rows × 21 columns</p>
</div>




```python
# *sort_values()* orders dataset by given parameter.
# Order by ascending price:

dataset.sort_values(by='price', ascending=True)
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
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>...</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1149</th>
      <td>3421079032</td>
      <td>20150217T000000</td>
      <td>75000.0</td>
      <td>1.0</td>
      <td>0.00</td>
      <td>670</td>
      <td>43377</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>3</td>
      <td>670</td>
      <td>0</td>
      <td>1966</td>
      <td>0</td>
      <td>98022</td>
      <td>47.2638</td>
      <td>-121.906</td>
      <td>1160</td>
      <td>42882</td>
    </tr>
    <tr>
      <th>15293</th>
      <td>40000362</td>
      <td>20140506T000000</td>
      <td>78000.0</td>
      <td>2.0</td>
      <td>1.00</td>
      <td>780</td>
      <td>16344</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>5</td>
      <td>780</td>
      <td>0</td>
      <td>1942</td>
      <td>0</td>
      <td>98168</td>
      <td>47.4739</td>
      <td>-122.280</td>
      <td>1700</td>
      <td>10387</td>
    </tr>
    <tr>
      <th>465</th>
      <td>8658300340</td>
      <td>20140523T000000</td>
      <td>80000.0</td>
      <td>1.0</td>
      <td>0.75</td>
      <td>430</td>
      <td>5050</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>4</td>
      <td>430</td>
      <td>0</td>
      <td>1912</td>
      <td>0</td>
      <td>98014</td>
      <td>47.6499</td>
      <td>-121.909</td>
      <td>1200</td>
      <td>7500</td>
    </tr>
    <tr>
      <th>16198</th>
      <td>3028200080</td>
      <td>20150324T000000</td>
      <td>81000.0</td>
      <td>2.0</td>
      <td>1.00</td>
      <td>730</td>
      <td>9975</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>5</td>
      <td>730</td>
      <td>0</td>
      <td>1943</td>
      <td>0</td>
      <td>98168</td>
      <td>47.4808</td>
      <td>-122.315</td>
      <td>860</td>
      <td>9000</td>
    </tr>
    <tr>
      <th>8274</th>
      <td>3883800011</td>
      <td>20141105T000000</td>
      <td>82000.0</td>
      <td>3.0</td>
      <td>1.00</td>
      <td>860</td>
      <td>10426</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6</td>
      <td>860</td>
      <td>0</td>
      <td>1954</td>
      <td>0</td>
      <td>98146</td>
      <td>47.4987</td>
      <td>-122.341</td>
      <td>1140</td>
      <td>11250</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1448</th>
      <td>8907500070</td>
      <td>20150413T000000</td>
      <td>5350000.0</td>
      <td>5.0</td>
      <td>5.00</td>
      <td>8000</td>
      <td>23985</td>
      <td>2.0</td>
      <td>0</td>
      <td>4</td>
      <td>...</td>
      <td>12</td>
      <td>6720</td>
      <td>1280</td>
      <td>2009</td>
      <td>0</td>
      <td>98004</td>
      <td>47.6232</td>
      <td>-122.220</td>
      <td>4600</td>
      <td>21750</td>
    </tr>
    <tr>
      <th>4411</th>
      <td>2470100110</td>
      <td>20140804T000000</td>
      <td>5570000.0</td>
      <td>5.0</td>
      <td>5.75</td>
      <td>9200</td>
      <td>35069</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>13</td>
      <td>6200</td>
      <td>3000</td>
      <td>2001</td>
      <td>0</td>
      <td>98039</td>
      <td>47.6289</td>
      <td>-122.233</td>
      <td>3560</td>
      <td>24345</td>
    </tr>
    <tr>
      <th>9254</th>
      <td>9208900037</td>
      <td>20140919T000000</td>
      <td>6885000.0</td>
      <td>6.0</td>
      <td>7.75</td>
      <td>9890</td>
      <td>31374</td>
      <td>2.0</td>
      <td>0</td>
      <td>4</td>
      <td>...</td>
      <td>13</td>
      <td>8860</td>
      <td>1030</td>
      <td>2001</td>
      <td>0</td>
      <td>98039</td>
      <td>47.6305</td>
      <td>-122.240</td>
      <td>4540</td>
      <td>42730</td>
    </tr>
    <tr>
      <th>3914</th>
      <td>9808700762</td>
      <td>20140611T000000</td>
      <td>7062500.0</td>
      <td>5.0</td>
      <td>4.50</td>
      <td>10040</td>
      <td>37325</td>
      <td>2.0</td>
      <td>1</td>
      <td>2</td>
      <td>...</td>
      <td>11</td>
      <td>7680</td>
      <td>2360</td>
      <td>1940</td>
      <td>2001</td>
      <td>98004</td>
      <td>47.6500</td>
      <td>-122.214</td>
      <td>3930</td>
      <td>25449</td>
    </tr>
    <tr>
      <th>7252</th>
      <td>6762700020</td>
      <td>20141013T000000</td>
      <td>7700000.0</td>
      <td>6.0</td>
      <td>8.00</td>
      <td>12050</td>
      <td>27600</td>
      <td>2.5</td>
      <td>0</td>
      <td>3</td>
      <td>...</td>
      <td>13</td>
      <td>8570</td>
      <td>3480</td>
      <td>1910</td>
      <td>1987</td>
      <td>98102</td>
      <td>47.6298</td>
      <td>-122.323</td>
      <td>3940</td>
      <td>8800</td>
    </tr>
  </tbody>
</table>
<p>21613 rows × 21 columns</p>
</div>




```python
# We can alter the dataset itself as well.
# Let's add an example column converting lot size to square meters and visualize the first 5 rows:

dataset['sqmt_lot'] = (dataset['sqft_lot'] * 0.092903)
dataset['sqmt_lot'].head()
```




    0    524.901950
    1    672.803526
    2    929.030000
    3    464.515000
    4    750.656240
    Name: sqmt_lot, dtype: float64




```python
# Creating a classification function:

def categorize(s):
    if s >= 1000:
        return 'Large'
    elif s >= 500:
        return 'Medium'
    elif s >= 250:
        return 'Small'
```


```python
# Adding a column with the classification labels and visualizing the first 5 rows:

dataset['cat_size'] = dataset['sqmt_lot'].apply(categorize)
dataset['cat_size'].head()
```




    0    Medium
    1    Medium
    2    Medium
    3     Small
    4    Medium
    Name: cat_size, dtype: object




```python
# Looking at the distribution of new values with *value_counts()*:

pd.value_counts(dataset['cat_size'])
```




    Medium    10214
    Large      5333
    Small      4460
    Name: cat_size, dtype: int64




```python
# To exclude data, we use *drop()*.
# Parameter "axis=1" defines that we want to exclude a column and not a row (index labels).
# Parameter "inplace=True" makes the change in memory, returning a copy of the dataset (no alteration on the original).

dataset.drop(['cat_size'], axis=1, inplace=True)
dataset.head()
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
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>...</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
      <th>sqmt_lot</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>20141013T000000</td>
      <td>221900.0</td>
      <td>3.0</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1180</td>
      <td>0</td>
      <td>1955</td>
      <td>0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
      <td>524.901950</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>20141209T000000</td>
      <td>538000.0</td>
      <td>3.0</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>2170</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
      <td>672.803526</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5631500400</td>
      <td>20150225T000000</td>
      <td>180000.0</td>
      <td>2.0</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>770</td>
      <td>0</td>
      <td>1933</td>
      <td>0</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
      <td>929.030000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2487200875</td>
      <td>20141209T000000</td>
      <td>604000.0</td>
      <td>4.0</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1050</td>
      <td>910</td>
      <td>1965</td>
      <td>0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
      <td>464.515000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>20150218T000000</td>
      <td>510000.0</td>
      <td>3.0</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1680</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
      <td>750.656240</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 22 columns</p>
</div>




```python
# We can drop data according to logical conditions as well.
# For example, let's exclude items with no bedrooms.

dataset.drop(dataset[dataset.bedrooms==0].index, inplace=True)
```


```python
# *iterrows()* is a generator function that iterates over dataset rows.

dataset.iterrows()
```




    <generator object DataFrame.iterrows at 0x00000212F95EBAC8>




```python
# Using *next()* we can manually iterate through each item:

next(dataset.iterrows())
```




    (0,
     id                    7129300520
     date             20141013T000000
     price                     221900
     bedrooms                       3
     bathrooms                      1
     sqft_living                 1180
     sqft_lot                    5650
     floors                         1
     waterfront                     0
     view                           0
     condition                      3
     grade                          7
     sqft_above                  1180
     sqft_basement                  0
     yr_built                    1955
     yr_renovated                   0
     zipcode                    98178
     lat                      47.5112
     long                    -122.257
     sqft_living15               1340
     sqft_lot15                  5650
     sqmt_lot                 524.902
     Name: 0, dtype: object)




```python
# Example for iterating through a set of rows:

for index, row in dataset.head(10).iterrows():
     print(index, row)
```

    0 id                    7129300520
    date             20141013T000000
    price                     221900
    bedrooms                       3
    bathrooms                      1
    sqft_living                 1180
    sqft_lot                    5650
    floors                         1
    waterfront                     0
    view                           0
    condition                      3
    grade                          7
    sqft_above                  1180
    sqft_basement                  0
    yr_built                    1955
    yr_renovated                   0
    zipcode                    98178
    lat                      47.5112
    long                    -122.257
    sqft_living15               1340
    sqft_lot15                  5650
    sqmt_lot                 524.902
    Name: 0, dtype: object
    1 id                    6414100192
    date             20141209T000000
    price                     538000
    bedrooms                       3
    bathrooms                   2.25
    sqft_living                 2570
    sqft_lot                    7242
    floors                         2
    waterfront                     0
    view                           0
    condition                      3
    grade                          7
    sqft_above                  2170
    sqft_basement                400
    yr_built                    1951
    yr_renovated                1991
    zipcode                    98125
    lat                       47.721
    long                    -122.319
    sqft_living15               1690
    sqft_lot15                  7639
    sqmt_lot                 672.804
    Name: 1, dtype: object
    2 id                    5631500400
    date             20150225T000000
    price                     180000
    bedrooms                       2
    bathrooms                      1
    sqft_living                  770
    sqft_lot                   10000
    floors                         1
    waterfront                     0
    view                           0
    condition                      3
    grade                          6
    sqft_above                   770
    sqft_basement                  0
    yr_built                    1933
    yr_renovated                   0
    zipcode                    98028
    lat                      47.7379
    long                    -122.233
    sqft_living15               2720
    sqft_lot15                  8062
    sqmt_lot                  929.03
    Name: 2, dtype: object
    3 id                    2487200875
    date             20141209T000000
    price                     604000
    bedrooms                       4
    bathrooms                      3
    sqft_living                 1960
    sqft_lot                    5000
    floors                         1
    waterfront                     0
    view                           0
    condition                      5
    grade                          7
    sqft_above                  1050
    sqft_basement                910
    yr_built                    1965
    yr_renovated                   0
    zipcode                    98136
    lat                      47.5208
    long                    -122.393
    sqft_living15               1360
    sqft_lot15                  5000
    sqmt_lot                 464.515
    Name: 3, dtype: object
    4 id                    1954400510
    date             20150218T000000
    price                     510000
    bedrooms                       3
    bathrooms                      2
    sqft_living                 1680
    sqft_lot                    8080
    floors                         1
    waterfront                     0
    view                           0
    condition                      3
    grade                          8
    sqft_above                  1680
    sqft_basement                  0
    yr_built                    1987
    yr_renovated                   0
    zipcode                    98074
    lat                      47.6168
    long                    -122.045
    sqft_living15               1800
    sqft_lot15                  7503
    sqmt_lot                 750.656
    Name: 4, dtype: object
    5 id                    7237550310
    date             20140512T000000
    price                  1.225e+06
    bedrooms                       4
    bathrooms                    4.5
    sqft_living                 5420
    sqft_lot                  101930
    floors                         1
    waterfront                     0
    view                           0
    condition                      3
    grade                         11
    sqft_above                  3890
    sqft_basement               1530
    yr_built                    2001
    yr_renovated                   0
    zipcode                    98053
    lat                      47.6561
    long                    -122.005
    sqft_living15               4760
    sqft_lot15                101930
    sqmt_lot                  9469.6
    Name: 5, dtype: object
    6 id                    1321400060
    date             20140627T000000
    price                     257500
    bedrooms                       3
    bathrooms                   2.25
    sqft_living                 1715
    sqft_lot                    6819
    floors                         2
    waterfront                     0
    view                           0
    condition                      3
    grade                          7
    sqft_above                  1715
    sqft_basement                  0
    yr_built                    1995
    yr_renovated                   0
    zipcode                    98003
    lat                      47.3097
    long                    -122.327
    sqft_living15               2238
    sqft_lot15                  6819
    sqmt_lot                 633.506
    Name: 6, dtype: object
    7 id                    2008000270
    date             20150115T000000
    price                     291850
    bedrooms                       3
    bathrooms                    1.5
    sqft_living                 1060
    sqft_lot                    9711
    floors                         1
    waterfront                     0
    view                           0
    condition                      3
    grade                          7
    sqft_above                  1060
    sqft_basement                  0
    yr_built                    1963
    yr_renovated                   0
    zipcode                    98198
    lat                      47.4095
    long                    -122.315
    sqft_living15               1650
    sqft_lot15                  9711
    sqmt_lot                 902.181
    Name: 7, dtype: object
    8 id                    2414600126
    date             20150415T000000
    price                     229500
    bedrooms                       3
    bathrooms                      1
    sqft_living                 1780
    sqft_lot                    7470
    floors                         1
    waterfront                     0
    view                           0
    condition                      3
    grade                          7
    sqft_above                  1050
    sqft_basement                730
    yr_built                    1960
    yr_renovated                   0
    zipcode                    98146
    lat                      47.5123
    long                    -122.337
    sqft_living15               1780
    sqft_lot15                  8113
    sqmt_lot                 693.985
    Name: 8, dtype: object
    9 id                    3793500160
    date             20150312T000000
    price                     323000
    bedrooms                       3
    bathrooms                    2.5
    sqft_living                 1890
    sqft_lot                    6560
    floors                         2
    waterfront                     0
    view                           0
    condition                      3
    grade                          7
    sqft_above                  1890
    sqft_basement                  0
    yr_built                    2003
    yr_renovated                   0
    zipcode                    98038
    lat                      47.3684
    long                    -122.031
    sqft_living15               2390
    sqft_lot15                  7570
    sqmt_lot                 609.444
    Name: 9, dtype: object
    


```python
# Showing only selected columns:

for index, row in dataset.head(10).iterrows():
     print(index, row['id'], row['yr_built'], row['sqmt_lot'])
```

    0 7129300520 1955 524.9019499999999
    1 6414100192 1951 672.803526
    2 5631500400 1933 929.03
    3 2487200875 1965 464.515
    4 1954400510 1987 750.65624
    5 7237550310 2001 9469.60279
    6 1321400060 1995 633.505557
    7 2008000270 1963 902.181033
    8 2414600126 1960 693.98541
    9 3793500160 2003 609.44368
    


```python
# It's possible to use *iterrows()* to alter data as well. Let's simulate a 15% price discount.
# Reviewing the first 5 rows before change:

dataset.price.head()
```




    0    221900.0
    1    538000.0
    2    180000.0
    3    604000.0
    4    510000.0
    Name: price, dtype: float64




```python
# Note the "at()" method:

for index, row in dataset.iterrows():
    dataset.at[index , 'price'] = row['price'] * 0.85
```


```python
# Result:

dataset.price.head()
```




    0    188615.0
    1    457300.0
    2    153000.0
    3    513400.0
    4    433500.0
    Name: price, dtype: float64




```python
# Alternatively, we can *itertuples()* to return values as tuples instead of lists.
# This function is generally faster than *iterrows()*.

for row in dataset.head().itertuples():
    print(row)
```

    Pandas(Index=0, id=7129300520, date='20141013T000000', price=188615.0, bedrooms=3.0, bathrooms=1.0, sqft_living=1180, sqft_lot=5650, floors=1.0, waterfront=0, view=0, condition=3, grade=7, sqft_above=1180, sqft_basement=0, yr_built=1955, yr_renovated=0, zipcode=98178, lat=47.5112, long=-122.257, sqft_living15=1340, sqft_lot15=5650, sqmt_lot=524.9019499999999)
    Pandas(Index=1, id=6414100192, date='20141209T000000', price=457300.0, bedrooms=3.0, bathrooms=2.25, sqft_living=2570, sqft_lot=7242, floors=2.0, waterfront=0, view=0, condition=3, grade=7, sqft_above=2170, sqft_basement=400, yr_built=1951, yr_renovated=1991, zipcode=98125, lat=47.721000000000004, long=-122.319, sqft_living15=1690, sqft_lot15=7639, sqmt_lot=672.803526)
    Pandas(Index=2, id=5631500400, date='20150225T000000', price=153000.0, bedrooms=2.0, bathrooms=1.0, sqft_living=770, sqft_lot=10000, floors=1.0, waterfront=0, view=0, condition=3, grade=6, sqft_above=770, sqft_basement=0, yr_built=1933, yr_renovated=0, zipcode=98028, lat=47.7379, long=-122.23299999999999, sqft_living15=2720, sqft_lot15=8062, sqmt_lot=929.03)
    Pandas(Index=3, id=2487200875, date='20141209T000000', price=513400.0, bedrooms=4.0, bathrooms=3.0, sqft_living=1960, sqft_lot=5000, floors=1.0, waterfront=0, view=0, condition=5, grade=7, sqft_above=1050, sqft_basement=910, yr_built=1965, yr_renovated=0, zipcode=98136, lat=47.5208, long=-122.39299999999999, sqft_living15=1360, sqft_lot15=5000, sqmt_lot=464.515)
    Pandas(Index=4, id=1954400510, date='20150218T000000', price=433500.0, bedrooms=3.0, bathrooms=2.0, sqft_living=1680, sqft_lot=8080, floors=1.0, waterfront=0, view=0, condition=3, grade=8, sqft_above=1680, sqft_basement=0, yr_built=1987, yr_renovated=0, zipcode=98074, lat=47.6168, long=-122.045, sqft_living15=1800, sqft_lot15=7503, sqmt_lot=750.65624)
    


```python
# Printing rows by column name with *itertuples()*:

for row in dataset.head().itertuples():
    print(row.id, row.bedrooms, row.price)
```

    7129300520 3.0 188615.0
    6414100192 3.0 457300.0
    5631500400 2.0 153000.0
    2487200875 4.0 513400.0
    1954400510 3.0 433500.0
    


```python
# Missing values are a common problem. They can affect data analysis and machine learning algorithms.
# Luckily, there are many ways to deal with this. Let's start by identifying where they are:

dataset.isnull().sum()
```




    id               0
    date             0
    price            0
    bedrooms         4
    bathrooms        0
    sqft_living      0
    sqft_lot         0
    floors           1
    waterfront       0
    view             0
    condition        0
    grade            0
    sqft_above       0
    sqft_basement    0
    yr_built         0
    yr_renovated     0
    zipcode          0
    lat              0
    long             0
    sqft_living15    0
    sqft_lot15       0
    sqmt_lot         0
    dtype: int64




```python
# *dropna()* works as a shortcut to remove rows where at least one value is missing:

dataset.dropna(inplace=True)
```


```python
# We can also remove only those rows or columns where every value is missing:

dataset.dropna(how='all', inplace=True)
```


```python
# Alternatively, we can fill up the missing values in various ways.
# Simply replacing the null values for "bedrooms" with "1":

dataset['bedrooms'].fillna(1, inplace=True)
```


```python
# Replacing null "floors" values with an average:

dataset['floors'].fillna(dataset['floors'].mean(), inplace=True)
```
