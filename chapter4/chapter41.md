# 数据处理

数据处理是数据分析，及后续数据挖掘中最重要的部分。
数据处理： 1. 可以提高数据的质量。2。能够较好支持数据分析。 

数据处理包括：
数据清洗、数据抽取、数据交换 和数据计算

## 1 数据清洗 
### 重复值的处理

1) DataFrame 中的 duplicated 方法检查是否有重复行。

```python
import numpy as np
import pandas as pd

df = pd.DataFrame({'age':pd.Series([26, 33, 78, 23, 26]),
                  'name':pd.Series(['aa', 'bb', 'cc', 'dd', 'aa'])})
print(df)
'''
   age name
0   26   aa
1   33   bb
2   78   cc
3   23   dd
4   26   aa
'''

print(df.duplicated())
'''
print(df['name'].duplicated()) # name 这一列是不是有重复；
0    False
1    False
2    False
3    False
4     True # 最后一行是重复的。
'''
df = df.drop_duplicates()
print(df)

'''
   age name
0   26   aa
1   33   bb
2   78   cc
3   23   dd
'''
```
通过去重， 可以有效减少重复数据带来数据分析的错误。

### 缺失值处理
假设有下列有缺失值矩阵

```Python
import numpy as np
import pandas as pd

df = pd.DataFrame(np.random.randint(low=2, high=10, size=(5, 6)))
print(df)
df.iloc[2:4, 1:3] = np.nan # 该矩阵的 第1行~第2行， 第0列到第2列 改为NAN
print(df)
'''
   0  1  2  3  4  5
0  9  9  6  7  3  8
1  6  8  3  4  5  2
2  5  9  4  4  4  7
3  3  3  2  8  8  4
4  4  3  6  4  7  4
============================

   0    1    2  3  4  5
0  9  9.0  6.0  7  3  8
1  6  8.0  3.0  4  5  2
2  5  NaN  NaN  4  4  7
3  3  NaN  NaN  8  8  4
4  4  3.0  6.0  4  7  4
'''
```
在该矩阵[2:4,1:3]处有缺失值。 

我们有几种处理方法：
#### 1. 数据补齐
```Python
df = df.fillna(method='pad')
# 用前一个数值填入
df = df.fillna(method='bfill')
# 用后一个数值填入
df = df.fillna(df.mean())
# 用均值来填补

df = df.fillna(df.mean()['A列':'B列'])
# 用B列的均值来代替A列的缺失值。
```

2. 数据删除
如果在海量的数据前提下， 如果通过df.isnull()来判断该数据中缺失值较少。 删除
不影响整体数据质量情况下，我们可以选择删除存在缺失值的行
```Python
df.dropna()
```
