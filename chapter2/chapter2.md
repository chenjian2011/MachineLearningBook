# 这一节主要将用到数据挖掘的主要基础库。

## 1. numpy 

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



## 3. matplotlib

