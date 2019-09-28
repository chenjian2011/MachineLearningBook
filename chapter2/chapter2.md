# 这一节主要将用到数据挖掘的主要基础库。

## 1. numpy 



Numpy 的矩阵计算（矩阵创建、矩阵计算）

### 1.1 numpy 基本概念

@@ numpy 主要做矩阵计算的一个基础库

numpy: 三个主要概念

```Python
基本的numpy
import numpy as np
array1 = np.array([[1,2,3],[2,3,4]]) 
print(array1)
[output]
[[1 2 3]
 [2 3 4]]  # 注意这个就是矩阵了。 
```

@@@
b = np.array([1,2,3,4])
b.shape # 4 ; 

```Python    
import numpy as np
b = np.array([1,2,3,4,5])
print(b.shape)
print(list(b.shape))

[output]
(5,)
[5]
```

ndim：维度
shape：行数和列数
size：元素个数

```Python
print('number of dim:',array.ndim)  # 维度

print('shape :',array.shape)    # 行数和列数

print('size:',array.size)   # 元素个数
[output]
number of dim: 2
shape : (2, 3)# 行数和列数；注意，这个是tuple类型
size: 6

```
### 1.2 创建 numpy 数组

@@@
创建指定数据的 数组： a = np.array([2,23,4],dtype=np.int)  

@@@ 
创建指定数据的矩阵：  a = np.array([[2,23,4],[2,32,4]])  

@@@   

注意！！！
a = np.array(1,2,3,4)    # WRONG

a = np.array([1,2,3,4])  # RIGHT 创建的时候是tuple内的list.  



@@@

```Python
v2 = np.arange(2,5)  # 等价于 v2 = np.array(2,5,1) (start,stop,delimiter)

print(v2.flatten()) # flatten函数，n x m 维矩阵 变为 n*m x 1 维
```

@@@

创建全0的矩阵

```Python
 a = np.zeros( [3,4] )  和  a = np.zeros((3,4)) 的效果是一样的。
 
[output]
array([[ 0.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  0.]])
```

@@@
创建全1的矩阵

```Python
a = np.ones( [3,4] )  和  a = np.ones((3,4)) 的效果是一样的。
```

@@@
创建全随机的矩阵

```Python
abc = np.random.randint(1000,9999)
mat1 = np.random.random(size=(3,4))# 创建一个 3x4的 0~1之间矩阵
print ('matrix generated from numpy.random.random is \n%s\n'%mat1)
mat2 = np.random.randint(low=1,high=20,size=(30,40))#创建30x40 1~19之间的矩阵
print ('matrix generated from numpy.random.random is \n%s\n'%mat2)
mat3 = np.random.randn(3,4) # 随机生成服从正态分布
print ('matrix generated from numpy.random.randn is \n%s\n'%mat3)
```

随机分布的矩阵也可以这样来显示

```Python
numpy.random.normal(loc=0.0, scale=1.0, size=None)
这里：
loc：float
    此概率分布的均值（对应着整个分布的中心centre）
scale：float
    此概率分布的标准差（对应于分布的宽度，scale越大越矮胖，scale越小，越瘦高）
size：int or tuple of ints
    输出的shape，默认为None，只输出一个值

```
那么输出1000个符合上述分布的随机数为：

```Python
num = numpy.random.normal(loc=0.0, scale=2.0,size=1000)
```

### 1.3 numpy数组切片
```Python
num = numpy.random.normal(loc=0.0, scale=2.0,size=1000)
slice = num[2:1000:14] #[start:end:step]
```

@@@
冒号 : 的解释：如果只放置一个参数，如 [2]，将返回与该索引相对应的单个元素。如果为 [2:]，表示从该</br>

索引开始以后的所有项都将被提取。如果使用了两个参数，如 [2:7]，那么则提取两个索引(不包括停止索

引)之间的项。</br>

如果是[::2],则默认全选， 间隔2；

### 1.4 高级索引

```Python
import numpy as np 
x = np.array([[1,  2],  [3,  4],  [5,  6]]) 
y = x[[0,1,2],  [0,1,0]]  
print (y)

输出结果为：[1  4  5]
```

```Python
import numpy as np 
x = np.array([[  0,  1,  2],[  3,  4,  5],[  6,  7,  8],[  9,  10,  11]])  

print ('我们的数组是：' )
print (x)
print ('\n')
rows = np.array([[0,0],[3,3]]) 
cols = np.array([[0,2],[0,2]]) 
y = x[rows,cols]  
print  ('这个数组的四个角元素是：')
print (y)

输出结果为：
我们的数组是：
[[ 0  1  2]
 [ 3  4  5]
 [ 6  7  8]
 [ 9 10 11]]

这个数组的四个角元素是：
[[ 0  2]
 [ 9 11]]
```

截取矩阵中的小矩阵或者向量
```Python
a=([[1,2,3],
        [4,5,6],
        [7,8,9]])

a[1][:] = [4,5,6] 第一行的所有元素

a[:,1] = [2,5,8]  第一列的所有元素

```


### 1.5 处理矩阵形状


```Python
mat1 = np.random.randint(1, 20, [3, 5])
mat3 = mat1.reshape(5, 3)
mat2 = mat1.resize(5,3)
```

resize()函数会改变mat1, reshape 不会改变。

取出部分矩阵

```Python
import numpy as np
mat1 = np.arange(12).reshape(3, 4)

mat2 = mat1[0:2,2:4]  # 注意这里 0:2 为零行~ 2-1行。   2:4 为第二列~4-1列。
矩阵 0行0列开始。
print(mat1)

print(mat2)
```


## 2. pandas
### pandas 基本概念及基本操作
Pandas 是基于 NumPy 的一个开源 Python 库，它被广泛用于快速分析数据，以及数据清洗和
准备等工作。它的名字来源是由“ Panel data”（面板数据，一个计量经济学名词）两个单词拼成
的。简单地说，你可以把 Pandas 看作是 Python 版的 Excel。

定义为：
a = Series([])


其中需要理解的两种数据结构
1）Series: 一维数组序列，与Numpy中的一维array类似。与 list结构也相类似。
2）DataFrame，二维表格型的数据结构。 我们处理很多数据， 大多数都是以这种形式存储显示的。 

```Python
import numpy as np
import pandas as pd

contries = ['usa', 'china', 'russia']
my_data = [100, 200, 150]
data = pd.Series(contries, my_data)
print(data)
[output]
100       usa
200     china
150    russia
dtype: object

# 也可以这样写
contries = ['usa', 'china', 'russia']
my_data = [100, 200, 150]
data = pd.Series(contries, index= my_data)# 这里的index表示索引， 可以省略。
print(data)
[output]
100       usa
200     china
150    russia
dtype: object

#注意， 当索引是字母时，需要这样写：
contries = ['usa', 'china', 'russia']
data = pd.Series(contries, index=['a','b','c'])# 索引只能是int和字符串类型。
print(data)
[output]
a       usa
b     china
b    russia
dtype: object


#或者省略索引直接写内容
A = Series([14, 12, 13]) 

[output]
0    14
1    12
2    13
dtype: int64


# 仔细看下列代码的区别

A = Series(['14', 12, 13], index=['a', 'b', 'c'])     
print(A['a'])
print(A[0])  
             
print(A['b'])
print(A[1])  

[output]
14
14
12
12
```
@@ 需要注意的是， pandas系列的下标在自定义的同时也有自己系统缺省的定义。




```python
A = Series(['first', 12, 13], index=['a', 'b', 'c'])  

#Series中，一列是元素，一列是索引。
A.append('2')# 出错

b = Series['2']
A.append(b)



# 需要注意的是append函数只是添加，需要有个变量接受这个添加
所以必不可少的一行代码是
A = A.append(b)
```
我们也可以通过查找索引值和元素值是否在该Series 中，返回布尔类型。

```Python
print('b' in A.index)      
print(12 in A.values)      
```

### 重新排序。 两种方法：

#### 1. 使用sort_index的方法
```Python
import pandas as pd                                             
from pandas import Series                                       
                                                                
x = pd.Series([4.5, 2.7, 1.2, -2.2], index=['d', 'c', 'f', 'b'])
print(x)                                                        
                                                                
x_x = x.sort_index(ascending=True)      #从小到大                        
                                                                
print(x_x)                                                      
                                                                
x_x_x = x.sort_values(ascending=False)  #从大到小                        
print(x_x_x)                                                    
```


#### 2. 使用reindex方法
```Python
import pandas as pd                                                    
from pandas import Series                                              
                                                                       
x = pd.Series([4.5, 2.7, 1.2, -2.2], index=['d', 'c', 'f', 'b'])       
print(x)                                                               
                                                                       
x1 = x.reindex(['a', 'b', 'c', 'd', 'e', 'f'])                         
print(x1)                                                              
                                                                       
x2 = x.reindex(['a', 'b', 'c', 'd', 'e', 'f'], fill_value=0)           
                                                                       
print(x2)                                                              
```

###DataFrames

我们可以把DataFrames 看做是一张数据表。 

我们想象一张数据库中的表。 每张表有表名， 而且表有它自己的字段名（列名）。 一行数据代表一个对象 等等。 
通过上句话， 我们在脑海中就能够想像得到我们是可以如何操作这张表了。

#### 初始化DataFrames

```Python
import pandas as pd                                                                                         
from pandas import DataFrame                                                                                
dataframe1 = pd.DataFrame({'name': ['tom', 'andy', 'peter'], 'age':[21, 22, 23], 'class':['a', 'b', 'a']})  
print(dataframe1)                                                                                           
[output]
    name  age class
0    tom   21     a
1   andy   22     b
2  peter   23     a
```
是不是和一张表很像？？  初始化DataFrame可以用一个字典数据类型来附初始值。

```Python
----------------查查查----------------------------
 直接获得该列的所有数值。(该字段的所有数值)
print(dataframe1['age']) 
返回的数值由列表格式组成

所以我们可以用以下代码来实现：
a = dataframe1['name']
print(a[1])
[output]
andy


获得一个数据块

a = dataframe1.iloc[1:3, 0:3]                              
print(a)                     

[output]
    name  age class
1   andy   22     b
2  peter   23     a

顾名思义： iloc就是根据行列的下标号进行查询的一个函数
比如下列：
a = dataframe1.iloc[:,0:3], 输出0~2列所有行。
a = dataframe1.iloc[0:3,:], 输出0~2行的所有列。
a = dataframe1.iloc[ 1,1],  输出第1行，第1列的数值。
      

--------------------改改改----------------------------
更改列表名：
df.rename(columns={'A': 'AA', 'C': 'CC'}, inplace=True)
将A 改为 AA.
print(df)   


---------------------------增增增------------------------------------



---------------------------删删删--------------------------------
test_dict_df.drop(['id'],axis=1) 删除列
test_dict_df.drop(['id'],axis=0) 删除行
```


@@ 在这里注意的是数据块iloc函数，函数内的参数为：[a,a-1行，b,b-1列]


#### Dataframe 文件读和写

注意！！ pandas 一般是导入有格式的数据。 比如csv,excel，格式化的txt文档以及数据库等等。 


这一节主要讲解DataFrame文件的读和写。 非常关键和重要

```Python
# 读取k盘的csv文档，分隔符为逗号。                                          
dt = pd.read_csv(r'k:\rz.csv', sep=',')   
#read_csv函数读取csv, 还有read_table # txt文档, read_xls,read_sql等等。

后面跟上分隔符 ，逗号。

print(dt)                                 

[output]
            学号        班级   姓名 性别  英语  体育  军训  数分  高代  解几
0   2308024241  23080242   成龙  男  76  78  77  40  23  60
1   2308024244  23080242   周怡  女  66  91  75  47  47  44
2   2308024251  23080242   张波  男  85  81  75  45  45  60
3   2308024249  23080242   朱浩  男  65  50  80  72  62  71
4   2308024219  23080242   封印  女  73  88  92  61  47  46
5   2308024201  23080242   迟培  男  60  50  89  71  76  71
6   2308024347  23080243   李华  女  67  61  84  61  65  78
7   2308024307  23080243   陈田  男  76  79  86  69  40  69
8   2308024326  23080243   余皓  男  66  67  85  65  61  71
9   2308024320  23080243   李嘉  女  62  作弊  90  60  67  77
10  2308024342  23080243  李上初  男  76  90  84  60  66  60
11  2308024310  23080243   郭窦  女  79  67  84  64  64  79
12  2308024435  23080244  姜毅涛  男  77  71  缺考  61  73  76
13  2308024432  23080244   赵宇  男  74  74  88  68  70  71
14  2308024446  23080244   周路  女  76  80  77  61  74  80
15  2308024421  23080244  林建祥  男  72  72  81  63  90  75
16  2308024433  23080244  李大强  男  79  76  77  78  70  70
17  2308024428  23080244  李侧通  男  64  96  91  69  出国  77
18  2308024402  23080244   王慧  女  73  74  93  70  71  75
19  2308024422  23080244  李晓亮  男  85  60  85  72  72  83
20  2308024201  23080242   迟培  男  60  50  89  71  76  71

```

读取excel 第几张 sheet




## 3. matplotlib

画三维图：

```Python
from mpl_toolkits import mplot3d
from sklearn.datasets import load_boston
from matplotlib import pyplot as plt

ax = plt.axes(projection='3d')
data = load_boston()
print(data['data'][:,7])
print(data['target'].size)

x = data['data'][:,6]
y = data['data'][:,7]
z = data['target']

ax.scatter3D(x, y, z, c=z, cmap='Greens')

plt.show()
```

画二维图：

```Python
from sklearn.datasets import load_boston
from matplotlib import pyplot as plt

ax = plt.axes(projection='3d')
data = load_boston()
print(data['data'][:,7])
print(data['target'].size)

x = data['data'][:,6]
y = data['data'][:,7]
z = data['target']

plt.plot(x,y,z,'ob')

plt.show()
```

