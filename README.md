# pandas


conexion a base de datos

```python
import pandas as pd
import pymysql
from sqlalchemy import create_engine
 
engine = create_engine('mysql+pymysql://user:pass@localhost:3306/DB')
 
df = pd.read_sql_query('select * from TABLE', engine)
print (df)
 
df.head()

```

filtrado de columnas

```python
df = pd.read_sql_query('select * from TABLE', engine, columns=['Columna_01','Columna_02'])
```

Guardar los datos en CSV delimitado por coma

```python

df.to_csv('ouput.csv', sep=',')

```
