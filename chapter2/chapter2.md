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

<<<<<<< HEAD

@@@

v2 = np.arange(2,5)  # 等价于 v2 = np.array(2,5,1) (start,stop,delimiter)

print(v2.flatten()) # flatten函数，n x m 维矩阵 变为 n*m x 1 维
=======
>>>>>>> refs/remotes/origin/master
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



## 2. pandas

## 3. matplotlib

