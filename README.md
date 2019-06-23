# JT
#依次判断：fixed_table, 当前python空间，sqlite数据库

#example

import pandas as pd

import numpy as np

import easysql2pd as es

import sqlite3

engine = sqlite3.connect(':memory:')
es.set_engine(engine)

def SQL(st=es.st_tables):
    return es.SQL(globals(),st)

aa = pd.DataFrame(np.arange(12))

bb = pd.DataFrame(np.arange(3))


cc = SQL('''
         copy ['aa'] to fixed_table
         ''')

cc = SQL('''
         select name from fixed_table
         ''')
print(cc)

cc = SQL('''

         select 'aa1' as tbl,count(*) as cnt from aa
         
           union all
           
         select 'bb1' as tbl,count(*) as cnt from bb
         
       '''
       )

print(cc)
