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
      <th>county_name</th>
      <th>precinct_name</th>
      <th>office_title</th>
      <th>candidate_ballot_name</th>
      <th>yes_votes</th>
      <th>no_votes</th>
      <th>Unnamed: 6</th>
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
no_absentee = original_data.loc[original_data['precinct_name'] != 'ABSENTEE']
```


```python
no_federal = no_absentee.loc[(no_absentee['precinct_name'] != 'FEDERAL')]
```


```python
no_provisional = no_federal.loc[(no_absentee['precinct_name'] != 'PROVISIONAL')]
```


```python
house1 = no_provisional[(no_provisional['office_title'] == 'State Representative - District 1')
                       | (no_provisional['office_title'] == 'Constitutional Amendment No. 1')]
```


```python
onehouse = house1[(house1['county_name'] == "Atchison")
                | (house1['county_name'] == "Holt")
                | (house1['county_name'] == "Nodaway")
                | (house1['county_name'] == "Worth")
               ]
```


```python
onecandidate = onehouse[(onehouse['candidate_ballot_name'] != "Paul Taylor")]
```


```python
onecandidate
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
      <th>county_name</th>
      <th>precinct_name</th>
      <th>office_title</th>
      <th>candidate_ballot_name</th>
      <th>yes_votes</th>
      <th>no_votes</th>
      <th>Unnamed: 6</th>
      <th>Unnamed: 7</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>144</th>
      <td>Atchison</td>
      <td>TARKIO</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>520</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>145</th>
      <td>Atchison</td>
      <td>ROCK PORT</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>646</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>146</th>
      <td>Atchison</td>
      <td>FAIRFAX</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>378</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>147</th>
      <td>Atchison</td>
      <td>WESTBORO</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>121</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>148</th>
      <td>Atchison</td>
      <td>WATSON</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>50</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>156</th>
      <td>Atchison</td>
      <td>TARKIO</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>329</td>
      <td>289.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>157</th>
      <td>Atchison</td>
      <td>ROCK PORT</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>431</td>
      <td>335.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>158</th>
      <td>Atchison</td>
      <td>FAIRFAX</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>203</td>
      <td>241.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>159</th>
      <td>Atchison</td>
      <td>WESTBORO</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>69</td>
      <td>76.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>160</th>
      <td>Atchison</td>
      <td>WATSON</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>37</td>
      <td>30.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4082</th>
      <td>Holt</td>
      <td>NORTHWEST</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>178</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4083</th>
      <td>Holt</td>
      <td>NORTHEAST</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>137</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4084</th>
      <td>Holt</td>
      <td>CENTRAL</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>588</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4085</th>
      <td>Holt</td>
      <td>SOUTHEAST-SOUTHWEST</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>633</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4092</th>
      <td>Holt</td>
      <td>NORTHWEST</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>134</td>
      <td>81.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4093</th>
      <td>Holt</td>
      <td>NORTHEAST</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>59</td>
      <td>101.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4094</th>
      <td>Holt</td>
      <td>CENTRAL</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>250</td>
      <td>389.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4095</th>
      <td>Holt</td>
      <td>SOUTHEAST-SOUTHWEST</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>333</td>
      <td>429.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7464</th>
      <td>Nodaway</td>
      <td>ATCHISON (CLEARMONT)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>123</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7465</th>
      <td>Nodaway</td>
      <td>GRANT (BARNARD)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>198</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7466</th>
      <td>Nodaway</td>
      <td>GREEN (QUITMAN)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>73</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7467</th>
      <td>Nodaway</td>
      <td>HOPKINS (HOPKINS)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>160</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7468</th>
      <td>Nodaway</td>
      <td>HUGHES (GRAHAM)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>174</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7469</th>
      <td>Nodaway</td>
      <td>INDEPENDENCE (PARNELL)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>91</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7470</th>
      <td>Nodaway</td>
      <td>JACKSON (RAVENWOOD)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>349</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7471</th>
      <td>Nodaway</td>
      <td>JEFFERSON (CONCEPTION JCT)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>224</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7472</th>
      <td>Nodaway</td>
      <td>LINCOLN (ELMO)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>131</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7473</th>
      <td>Nodaway</td>
      <td>MONROE (SKIDMORE)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>137</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7474</th>
      <td>Nodaway</td>
      <td>NODAWAY (BURL JCT)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>221</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7475</th>
      <td>Nodaway</td>
      <td>UNION (PICKERING)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>146</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7476</th>
      <td>Nodaway</td>
      <td>WASHINGTON (GUILFORD)</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>118</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7477</th>
      <td>Nodaway</td>
      <td>WHITE CLOUD</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>174</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7478</th>
      <td>Nodaway</td>
      <td>POLK A-POLK D</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>1139</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7479</th>
      <td>Nodaway</td>
      <td>POLK E</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>492</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7480</th>
      <td>Nodaway</td>
      <td>POLK B-POLK C</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>1343</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7540</th>
      <td>Nodaway</td>
      <td>ATCHISON (CLEARMONT)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>84</td>
      <td>75.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7541</th>
      <td>Nodaway</td>
      <td>GRANT (BARNARD)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>132</td>
      <td>113.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7542</th>
      <td>Nodaway</td>
      <td>GREEN (QUITMAN)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>42</td>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7543</th>
      <td>Nodaway</td>
      <td>HOPKINS (HOPKINS)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>113</td>
      <td>106.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7544</th>
      <td>Nodaway</td>
      <td>HUGHES (GRAHAM)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>72</td>
      <td>120.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7545</th>
      <td>Nodaway</td>
      <td>INDEPENDENCE (PARNELL)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>61</td>
      <td>50.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7546</th>
      <td>Nodaway</td>
      <td>JACKSON (RAVENWOOD)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>170</td>
      <td>216.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7547</th>
      <td>Nodaway</td>
      <td>JEFFERSON (CONCEPTION JCT)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>145</td>
      <td>147.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7548</th>
      <td>Nodaway</td>
      <td>LINCOLN (ELMO)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>62</td>
      <td>88.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7549</th>
      <td>Nodaway</td>
      <td>MONROE (SKIDMORE)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>84</td>
      <td>93.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7550</th>
      <td>Nodaway</td>
      <td>NODAWAY (BURL JCT)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>150</td>
      <td>135.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7551</th>
      <td>Nodaway</td>
      <td>UNION (PICKERING)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>74</td>
      <td>96.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7552</th>
      <td>Nodaway</td>
      <td>WASHINGTON (GUILFORD)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>50</td>
      <td>89.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7553</th>
      <td>Nodaway</td>
      <td>WHITE CLOUD</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>99</td>
      <td>103.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7554</th>
      <td>Nodaway</td>
      <td>POLK A-POLK D</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>1017</td>
      <td>696.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7555</th>
      <td>Nodaway</td>
      <td>POLK E</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>295</td>
      <td>290.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7556</th>
      <td>Nodaway</td>
      <td>POLK B-POLK C</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>1039</td>
      <td>756.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13643</th>
      <td>Worth</td>
      <td>ALLEN</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>61</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13644</th>
      <td>Worth</td>
      <td>EAST FLETCHALL</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>144</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13645</th>
      <td>Worth</td>
      <td>GREENE</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>73</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13646</th>
      <td>Worth</td>
      <td>MIDDLE FORK</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>62</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13647</th>
      <td>Worth</td>
      <td>SMITH</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>72</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13648</th>
      <td>Worth</td>
      <td>WEST FLETCHALL</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>190</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13649</th>
      <td>Worth</td>
      <td>WEST UNION</td>
      <td>State Representative - District 1</td>
      <td>Allen Andrews</td>
      <td>125</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13675</th>
      <td>Worth</td>
      <td>ALLEN</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>25</td>
      <td>45.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13676</th>
      <td>Worth</td>
      <td>EAST FLETCHALL</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>77</td>
      <td>78.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13677</th>
      <td>Worth</td>
      <td>GREENE</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>23</td>
      <td>53.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13678</th>
      <td>Worth</td>
      <td>MIDDLE FORK</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>28</td>
      <td>50.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13679</th>
      <td>Worth</td>
      <td>SMITH</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>37</td>
      <td>44.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13680</th>
      <td>Worth</td>
      <td>WEST FLETCHALL</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>86</td>
      <td>116.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13681</th>
      <td>Worth</td>
      <td>WEST UNION</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>53</td>
      <td>76.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
justa1 = onecandidate[(onecandidate['office_title'] == "Constitutional Amendment No. 1")]
```


```python
justa1
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
      <th>county_name</th>
      <th>precinct_name</th>
      <th>office_title</th>
      <th>candidate_ballot_name</th>
      <th>yes_votes</th>
      <th>no_votes</th>
      <th>Unnamed: 6</th>
      <th>Unnamed: 7</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>156</th>
      <td>Atchison</td>
      <td>TARKIO</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>329</td>
      <td>289.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>157</th>
      <td>Atchison</td>
      <td>ROCK PORT</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>431</td>
      <td>335.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>158</th>
      <td>Atchison</td>
      <td>FAIRFAX</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>203</td>
      <td>241.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>159</th>
      <td>Atchison</td>
      <td>WESTBORO</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>69</td>
      <td>76.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>160</th>
      <td>Atchison</td>
      <td>WATSON</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>37</td>
      <td>30.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4092</th>
      <td>Holt</td>
      <td>NORTHWEST</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>134</td>
      <td>81.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4093</th>
      <td>Holt</td>
      <td>NORTHEAST</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>59</td>
      <td>101.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4094</th>
      <td>Holt</td>
      <td>CENTRAL</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>250</td>
      <td>389.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4095</th>
      <td>Holt</td>
      <td>SOUTHEAST-SOUTHWEST</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>333</td>
      <td>429.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7540</th>
      <td>Nodaway</td>
      <td>ATCHISON (CLEARMONT)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>84</td>
      <td>75.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7541</th>
      <td>Nodaway</td>
      <td>GRANT (BARNARD)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>132</td>
      <td>113.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7542</th>
      <td>Nodaway</td>
      <td>GREEN (QUITMAN)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>42</td>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7543</th>
      <td>Nodaway</td>
      <td>HOPKINS (HOPKINS)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>113</td>
      <td>106.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7544</th>
      <td>Nodaway</td>
      <td>HUGHES (GRAHAM)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>72</td>
      <td>120.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7545</th>
      <td>Nodaway</td>
      <td>INDEPENDENCE (PARNELL)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>61</td>
      <td>50.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7546</th>
      <td>Nodaway</td>
      <td>JACKSON (RAVENWOOD)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>170</td>
      <td>216.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7547</th>
      <td>Nodaway</td>
      <td>JEFFERSON (CONCEPTION JCT)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>145</td>
      <td>147.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7548</th>
      <td>Nodaway</td>
      <td>LINCOLN (ELMO)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>62</td>
      <td>88.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7549</th>
      <td>Nodaway</td>
      <td>MONROE (SKIDMORE)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>84</td>
      <td>93.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7550</th>
      <td>Nodaway</td>
      <td>NODAWAY (BURL JCT)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>150</td>
      <td>135.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7551</th>
      <td>Nodaway</td>
      <td>UNION (PICKERING)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>74</td>
      <td>96.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7552</th>
      <td>Nodaway</td>
      <td>WASHINGTON (GUILFORD)</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>50</td>
      <td>89.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7553</th>
      <td>Nodaway</td>
      <td>WHITE CLOUD</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>99</td>
      <td>103.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7554</th>
      <td>Nodaway</td>
      <td>POLK A-POLK D</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>1017</td>
      <td>696.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7555</th>
      <td>Nodaway</td>
      <td>POLK E</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>295</td>
      <td>290.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7556</th>
      <td>Nodaway</td>
      <td>POLK B-POLK C</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>1039</td>
      <td>756.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13675</th>
      <td>Worth</td>
      <td>ALLEN</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>25</td>
      <td>45.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13676</th>
      <td>Worth</td>
      <td>EAST FLETCHALL</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>77</td>
      <td>78.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13677</th>
      <td>Worth</td>
      <td>GREENE</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>23</td>
      <td>53.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13678</th>
      <td>Worth</td>
      <td>MIDDLE FORK</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>28</td>
      <td>50.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13679</th>
      <td>Worth</td>
      <td>SMITH</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>37</td>
      <td>44.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13680</th>
      <td>Worth</td>
      <td>WEST FLETCHALL</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>86</td>
      <td>116.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13681</th>
      <td>Worth</td>
      <td>WEST UNION</td>
      <td>Constitutional Amendment No. 1</td>
      <td>NaN</td>
      <td>53</td>
      <td>76.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
justa1.yes_votes.sum()
```




    5863




```python
h1yes = justa1.yes_votes.sum()
```


```python
justa1.no_votes.sum()
```




    5661.0




```python
h1no = justa1.no_votes.sum()
```


```python
house_district1_percentage = h1yes / (h1yes + h1no)
```


```python
house_district1_percentage * 100
```




    50.876431794515796




```python
pd.set_option('display.max_rows', None)
```


```python
house1.yes_votes.sum()
```




    1388066



"9,271" Verified in Microsoft Excel 


```python
house2 = no_provisional[(no_provisional['office_title'] == 'State Representative - District 2')]
```


```python
house2
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
      <th>county_name</th>
      <th>precinct_name</th>
      <th>office_title</th>
      <th>candidate_ballot_name</th>
      <th>yes_votes</th>
      <th>no_votes</th>
      <th>Unnamed: 6</th>
      <th>Unnamed: 7</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2769</th>
      <td>Daviess</td>
      <td>ALTAMONT</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>483</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2770</th>
      <td>Daviess</td>
      <td>GALLATIN</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>711</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2771</th>
      <td>Daviess</td>
      <td>JAMESON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>172</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2772</th>
      <td>Daviess</td>
      <td>JAMESPORT</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>332</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2773</th>
      <td>Daviess</td>
      <td>PATTONSBURG</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>340</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2774</th>
      <td>Daviess</td>
      <td>WINSTON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>413</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2801</th>
      <td>De Kalb</td>
      <td>ADAMS</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>220</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2802</th>
      <td>De Kalb</td>
      <td>COLFAX</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>263</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2803</th>
      <td>De Kalb</td>
      <td>GRAND RIVER</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>662</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2804</th>
      <td>De Kalb</td>
      <td>POLK</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>279</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2805</th>
      <td>De Kalb</td>
      <td>SHERMAN</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>199</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2806</th>
      <td>De Kalb</td>
      <td>NORTH WASHINGTON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>243</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2807</th>
      <td>De Kalb</td>
      <td>SOUTH WASHINGTON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>451</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2808</th>
      <td>De Kalb</td>
      <td>JUNE CONLEY BUILDING</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>815</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3384</th>
      <td>Gentry</td>
      <td>ATHENS NORTH AND SOUTH</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>674</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3385</th>
      <td>Gentry</td>
      <td>BOGLE GENTRY</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>70</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3386</th>
      <td>Gentry</td>
      <td>COOPER EAST AND WEST</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>514</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3387</th>
      <td>Gentry</td>
      <td>COOPER DARLINGTON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>58</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3388</th>
      <td>Gentry</td>
      <td>HOWARD LONESTAR</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>44</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3389</th>
      <td>Gentry</td>
      <td>HUGGINS CARMACK</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>59</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3390</th>
      <td>Gentry</td>
      <td>JACKSON EAST &amp;WEST</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>416</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3391</th>
      <td>Gentry</td>
      <td>MILLER BERLIN</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>87</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3392</th>
      <td>Gentry</td>
      <td>MILLER MCFALL</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>65</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3393</th>
      <td>Gentry</td>
      <td>WILSON ALANTHUS</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>70</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3973</th>
      <td>Harrison</td>
      <td>BETHANY</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>1003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3974</th>
      <td>Harrison</td>
      <td>CAINSVILLE</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>217</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3975</th>
      <td>Harrison</td>
      <td>GILMAN CITY</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>203</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3976</th>
      <td>Harrison</td>
      <td>EAGLEVILLE</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>342</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3977</th>
      <td>Harrison</td>
      <td>NEW HAMPTON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>244</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3978</th>
      <td>Harrison</td>
      <td>RIDGEWAY</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>211</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
house2
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
      <th>county_name</th>
      <th>precinct_name</th>
      <th>office_title</th>
      <th>candidate_ballot_name</th>
      <th>yes_votes</th>
      <th>no_votes</th>
      <th>Unnamed: 6</th>
      <th>Unnamed: 7</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2769</th>
      <td>Daviess</td>
      <td>ALTAMONT</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>483</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2770</th>
      <td>Daviess</td>
      <td>GALLATIN</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>711</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2771</th>
      <td>Daviess</td>
      <td>JAMESON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>172</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2772</th>
      <td>Daviess</td>
      <td>JAMESPORT</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>332</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2773</th>
      <td>Daviess</td>
      <td>PATTONSBURG</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>340</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2774</th>
      <td>Daviess</td>
      <td>WINSTON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>413</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2801</th>
      <td>De Kalb</td>
      <td>ADAMS</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>220</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2802</th>
      <td>De Kalb</td>
      <td>COLFAX</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>263</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2803</th>
      <td>De Kalb</td>
      <td>GRAND RIVER</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>662</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2804</th>
      <td>De Kalb</td>
      <td>POLK</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>279</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2805</th>
      <td>De Kalb</td>
      <td>SHERMAN</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>199</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2806</th>
      <td>De Kalb</td>
      <td>NORTH WASHINGTON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>243</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2807</th>
      <td>De Kalb</td>
      <td>SOUTH WASHINGTON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>451</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2808</th>
      <td>De Kalb</td>
      <td>JUNE CONLEY BUILDING</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>815</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3384</th>
      <td>Gentry</td>
      <td>ATHENS NORTH AND SOUTH</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>674</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3385</th>
      <td>Gentry</td>
      <td>BOGLE GENTRY</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>70</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3386</th>
      <td>Gentry</td>
      <td>COOPER EAST AND WEST</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>514</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3387</th>
      <td>Gentry</td>
      <td>COOPER DARLINGTON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>58</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3388</th>
      <td>Gentry</td>
      <td>HOWARD LONESTAR</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>44</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3389</th>
      <td>Gentry</td>
      <td>HUGGINS CARMACK</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>59</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3390</th>
      <td>Gentry</td>
      <td>JACKSON EAST &amp;WEST</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>416</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3391</th>
      <td>Gentry</td>
      <td>MILLER BERLIN</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>87</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3392</th>
      <td>Gentry</td>
      <td>MILLER MCFALL</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>65</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3393</th>
      <td>Gentry</td>
      <td>WILSON ALANTHUS</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>70</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3973</th>
      <td>Harrison</td>
      <td>BETHANY</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>1003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3974</th>
      <td>Harrison</td>
      <td>CAINSVILLE</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>217</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3975</th>
      <td>Harrison</td>
      <td>GILMAN CITY</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>203</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3976</th>
      <td>Harrison</td>
      <td>EAGLEVILLE</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>342</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3977</th>
      <td>Harrison</td>
      <td>NEW HAMPTON</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>244</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3978</th>
      <td>Harrison</td>
      <td>RIDGEWAY</td>
      <td>State Representative - District 2</td>
      <td>J. Eggleston</td>
      <td>211</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>


