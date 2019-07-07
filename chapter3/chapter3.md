# 文件操作


## 1. 读取文件

### 1.1 读取文本(txt) 用 逗号隔开。

```Python
import pandas as pd
my_data = pd.read_csv('d:\\train_data.txt', sep='\t')
print(my_data)
```

### 1.2 读取文本 csv 

```Python
import pandas as pd
my_data = pd.read_csv('d:\\train_data.csv')
print(my_data)
```

### 1.3 读取数据库 mysql

