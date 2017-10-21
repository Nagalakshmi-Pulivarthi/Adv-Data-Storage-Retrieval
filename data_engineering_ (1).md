

```python
import pandas as pd
import csv
import sqlite3
```


```python
station_file=("hawaii_stations.csv")
station_file_df=pd.read_csv(station_file)
station_file_df.dropna(how='any',inplace=True)
station_file_df.to_csv("clean_hawaii_stattion.csv",encoding="utf-8",index=False)
```


```python
measurement_file=("hawaii_measurements.csv")
messureemnt_file_df=pd.read_csv(measurement_file)
messureemnt_file_df.dropna(how='any',inplace=True)
messureemnt_file_df.to_csv("clean_hawaii_measurements.csv",encoding='utf-8',index=False)
```
