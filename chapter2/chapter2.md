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
创建全0的矩阵
```Python
 a = np.zeros( [3,4] )  和  a = np.zeros((3,4)) 的效果是一样的。
[output]
array([[ 0.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  0.]])
```


## 2. pandas

## 3. matplotlib

