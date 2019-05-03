# JT

#example

#!!!must import as  "es"!!!
import easysql2pd as es

import pandas as pd

import numpy as np



aa = pd.DataFrame(np.arange(2))

xx = pd.DataFrame(np.arange(3))

es.s = '''select 'aa' as tbl ,count(*) as cnt from aa 
        union all 
        select 'xx' as tbl, count(*) as cnt from xx '''


bb = eval(es.ss)

print(bb)
