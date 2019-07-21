# pandas

## CONEXION ENTRADA / SALIDA

### LEER ARCHIVO CSV
```python
import pandas as pd
pd.read_csv('table.csv', sep=';')
```
### LEER BASE DE DATOS MYSQ
```python
import pandas as pd
import pymysql
from sqlalchemy import create_engine
 
engine = create_engine('mysql+pymysql://root:tronicanet@localhost:3306/information_schema')
df = pd.read_sql_query("select `TABLE_NAME` from TABLE_CONSTRAINTS where `CONSTRAINT_SCHEMA`='mqtt'", engine)
display (df)
```
### LEER INFLUXDB

### GUARDAR CSV

### GUARDAR EXCEL

## COLUMNAS

### Dataframe format

```
>>> d = {'col1': [1, 2], 'col2': [3, 4]}
>>> df = pd.DataFrame(data=d)
>>> df
   col1  col2
0     1     3
1     2     4
```

### Conexion a base de datos MYSQL

```python
import pandas as pd
import pymysql
from sqlalchemy import create_engine
 
engine = create_engine('mysql+pymysql://user:pass@localhost:3306/DB')
 
df = pd.read_sql_query('select * from TABLE', engine)
print (df)
 
df.head()

```

### filtrado de columnas

```python
df = pd.read_sql_query('select * from TABLE', engine, columns=['Columna_01','Columna_02'])
```

### Guardar los datos en archivo CSV delimitado por coma

```python

df.to_csv('ouput.csv', sep=',')

```


### Conexion a archivo CSV

Leer archivo csv proveniente desde una url

```python
import requests
import pandas as pd
from pandas.compat import StringIO
 
url = 'https://www.web.com/archivo.csv'
 
r = requests.get(url)
df = pd.read_csv(StringIO(r.text), sep=',')
```

### Leer archivo csv desde url y guardar los datos en BD

```python
import requests
import pandas as pd
from pandas.compat import StringIO
import pymysql
from sqlalchemy import create_engine
 
engine = create_engine('mysql+pymysql://user:pass@localhost:3306/DB')
 
url = 'http://www.web.com/archivo.csv'
 
r = requests.get(url)
df = pd.read_csv(StringIO(r.text), sep='|')
 
with engine.connect() as conn, conn.begin():
    df.to_sql('tabla1', conn, if_exists='replace')

```

### json to panda
```
https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.io.json.json_normalize.html
```


LINK  

http://numba.pydata.org/numba-doc/latest/user/5minguide.html
