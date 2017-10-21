

```python
from sqlalchemy import create_engine
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy import Column, Integer, String, Float 
from sqlalchemy import create_engine
from sqlalchemy.ext.automap import automap_base
import pymysql
pymysql.install_as_MySQLdb()
from sqlalchemy.orm import session
import sqlite3
from datetime import datetime,timedelta

```


```python
Base = declarative_base()
class Measurement(Base):
    __tablename__ = 'Measurement'
    Id=Column(Integer,primary_key=True)
    station=Column(String(255))
    date=Column(String(255))
    prcp=Column(Float)
    tobs=Column(Integer)
    

```


```python
engine=create_engine("sqlite:///hawaii1.sqlite")
conn=engine.connect()
conn.execute("drop table Measurement")

Base.metadata.create_all(conn)
session=Session(bind=engine)
```


```python
df = pandas.read_csv("clean_hawaii_measurements.csv")
df.to_sql("Measurement", conn, if_exists='append', index=False)
cur = conn.execute("select count(*) c from Measurement limit 5")

for name in cur:
    print(name)
```

    (18103,)
    


```python
Base = declarative_base()
class Station(Base):
    __tablename__="Station"
    Id=Column(Integer,primary_key=True)
    station=Column(String(255))
    name=Column(String(255))
    latitude=Column(Float)
    longitude=Column(Float)
    elevation=Column(Float)
```


```python
engine=create_engine("sqlite:///hawaii1.sqlite")
conn=engine.connect()
conn.execute("drop table Station")

Base.metadata.create_all(conn)
session=Session(bind=engine)
```


```python
df = pandas.read_csv("clean_hawaii_stattion.csv")
df.to_sql("Station", conn, if_exists='append', index=False)
cur = conn.execute("select * from Station ")
for name in cur:
    print(name)
```

    (1, 'USC00519397', 'WAIKIKI 717.2, HI US', 21.2716, -157.8168, 3.0)
    (2, 'USC00513117', 'KANEOHE 838.1, HI US', 21.4234, -157.8015, 14.6)
    (3, 'USC00514830', 'KUALOA RANCH HEADQUARTERS 886.9, HI US', 21.5213, -157.8374, 7.0)
    (4, 'USC00517948', 'PEARL CITY, HI US', 21.3934, -157.9751, 11.9)
    (5, 'USC00518838', 'UPPER WAHIAWA 874.3, HI US', 21.4992, -158.0111, 306.6)
    (6, 'USC00519523', 'WAIMANALO EXPERIMENTAL FARM, HI US', 21.33556, -157.71139, 19.5)
    (7, 'USC00519281', 'WAIHEE 837.5, HI US', 21.45167, -157.84888999999995, 32.9)
    (8, 'USC00511918', 'HONOLULU OBSERVATORY 702.2, HI US', 21.3152, -157.9992, 0.9)
    (9, 'USC00516128', 'MANOA LYON ARBO 785.2, HI US', 21.3331, -157.8025, 152.4)
    


```python

```
