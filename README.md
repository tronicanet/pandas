# pandas


conexion a base de datos

```python
import pandas as pd
import pymysql
from sqlalchemy import create_engine
 
engine = create_engine('mysql+pymysql://user:pass@localhost:3306/DB')
 
df = pd.read_sql_query('select * from cdl_sitio', engine)
print (df)
 
df.head()

```
