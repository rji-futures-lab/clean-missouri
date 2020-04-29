```python
import pandas as pd
import numpy as np
```


```python
pd.read_csv("/Users/ashlynohara/Desktop/cleanmopython/cleanmissouri/data.csv")
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
      <th>County Name</th>
      <th>Precinct Name</th>
      <th>Office Title</th>
      <th>Candidate Ballot Name</th>
      <th>Yes votes</th>
      <th>No votes</th>
      <th>Precident Address</th>
      <th>Unnamed: 7</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Adair</td>
      <td>SOUTHWEST 1</td>
      <td>State Senator - District 18</td>
      <td>Cindy O'Laughlin</td>
      <td>283</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Adair</td>
      <td>SOUTHEAST 2</td>
      <td>State Senator - District 18</td>
      <td>Cindy O'Laughlin</td>
      <td>635</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Adair</td>
      <td>SOUTHEAST 3</td>
      <td>State Senator - District 18</td>
      <td>Cindy O'Laughlin</td>
      <td>194</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adair</td>
      <td>SOUTHEAST 4</td>
      <td>State Senator - District 18</td>
      <td>Cindy O'Laughlin</td>
      <td>325</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Adair</td>
      <td>NORTHEAST 5</td>
      <td>State Senator - District 18</td>
      <td>Cindy O'Laughlin</td>
      <td>396</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
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
    </tr>
    <tr>
      <th>13698</th>
      <td>Wright</td>
      <td>HARTVILLE</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>300</td>
      <td>399.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13699</th>
      <td>Wright</td>
      <td>LITTLE CREEK</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>164</td>
      <td>193.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13700</th>
      <td>Wright</td>
      <td>MANES</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>115</td>
      <td>208.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13701</th>
      <td>Wright</td>
      <td>GROVESPRING</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>230</td>
      <td>358.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13702</th>
      <td>Wright</td>
      <td>ABSENTEE</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>170</td>
      <td>182.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>13703 rows × 8 columns</p>
</div>




```python
original_data = pd.read_csv("/Users/ashlynohara/Desktop/cleanmopython/cleanmissouri/data.csv")
```


```python
original_data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 13703 entries, 0 to 13702
    Data columns (total 8 columns):
     #   Column                 Non-Null Count  Dtype  
    ---  ------                 --------------  -----  
     0   County Name            13703 non-null  object 
     1   Precinct Name          13703 non-null  object 
     2   Office Title           13703 non-null  object 
     3   Candidate Ballot Name  11161 non-null  object 
     4   Yes votes              13703 non-null  object 
     5   No votes               3199 non-null   float64
     6   Precident Address      0 non-null      float64
     7   Unnamed: 7             1 non-null      float64
    dtypes: float64(3), object(5)
    memory usage: 856.6+ KB



```python
original_data['Office Title']
```




    0           State Senator - District 18
    1           State Senator - District 18
    2           State Senator - District 18
    3           State Senator - District 18
    4           State Senator - District 18
                          ...              
    13698    Constitutional Amendment No. 1
    13699    Constitutional Amendment No. 1
    13700    Constitutional Amendment No. 1
    13701    Constitutional Amendment No. 1
    13702    Constitutional Amendment No. 1
    Name: Office Title, Length: 13703, dtype: object




```python
original_data['Office Title'].value_counts()
```




    Constitutional Amendment No. 1         3199
    State Senator - District 24             435
    State Senator - District 6              322
    State Senator - District 12             300
    State Senator - District 18             300
                                           ... 
    State Representative - District 21       17
    State Representative - District 25       16
    State Representative - District 156      15
    State Representative - District 24       15
    State Representative - District 122       7
    Name: Office Title, Length: 181, dtype: int64




```python
original_data[(original_data['County Name'] == 'Adair') 
              & (original_data['Office Title'] == "State Representative - District 4")
              & (original_data['Candidate Ballot Name'] == "Greg Sharpe")
             ]
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
      <th>County Name</th>
      <th>Precinct Name</th>
      <th>Office Title</th>
      <th>Candidate Ballot Name</th>
      <th>Yes votes</th>
      <th>No votes</th>
      <th>Precident Address</th>
      <th>Unnamed: 7</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>48</th>
      <td>Adair</td>
      <td>SOUTHWEST 1</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>49</th>
      <td>Adair</td>
      <td>SOUTHEAST 2</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50</th>
      <td>Adair</td>
      <td>SOUTHEAST 3</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>51</th>
      <td>Adair</td>
      <td>SOUTHEAST 4</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>52</th>
      <td>Adair</td>
      <td>NORTHEAST 5</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>53</th>
      <td>Adair</td>
      <td>NORTHEAST 6</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>54</th>
      <td>Adair</td>
      <td>TSU</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>55</th>
      <td>Adair</td>
      <td>RURAL BENTON</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>607</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>56</th>
      <td>Adair</td>
      <td>BRASHEAR</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>577</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>57</th>
      <td>Adair</td>
      <td>NOVINGER</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>73</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>58</th>
      <td>Adair</td>
      <td>ABSENTEE</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>234</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>59</th>
      <td>Adair</td>
      <td>FEDERAL</td>
      <td>State Representative - District 4</td>
      <td>Greg Sharpe</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
original_data[(original_data['County Name'] == 'Adair') 
              & (original_data['Office Title'] == "State Representative - District 3")
              & (original_data['Candidate Ballot Name'] == "Danny Busick")
             ]
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
      <th>County Name</th>
      <th>Precinct Name</th>
      <th>Office Title</th>
      <th>Candidate Ballot Name</th>
      <th>Yes votes</th>
      <th>No votes</th>
      <th>Precident Address</th>
      <th>Unnamed: 7</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>24</th>
      <td>Adair</td>
      <td>SOUTHWEST 1</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>258</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Adair</td>
      <td>SOUTHEAST 2</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>620</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Adair</td>
      <td>SOUTHEAST 3</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>187</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Adair</td>
      <td>SOUTHEAST 4</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>306</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Adair</td>
      <td>NORTHEAST 5</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>373</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Adair</td>
      <td>NORTHEAST 6</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>521</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Adair</td>
      <td>TSU</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>65</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Adair</td>
      <td>RURAL BENTON</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>418</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Adair</td>
      <td>BRASHEAR</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>33</th>
      <td>Adair</td>
      <td>NOVINGER</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>537</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>34</th>
      <td>Adair</td>
      <td>ABSENTEE</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>376</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>35</th>
      <td>Adair</td>
      <td>FEDERAL</td>
      <td>State Representative - District 3</td>
      <td>Danny Busick</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
