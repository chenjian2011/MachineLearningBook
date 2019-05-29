# 这一章节主要讲述Python 的 普通语法


## 1. Python 数据类型
### 1.1 基本数据类型
###  1.1.1 Python 中， 数据类型总共有4种：
 整数|长整数|浮点数|复数

在Python代码中表示成：
```Python

a = 10
b = 10e5
c = 22.8
d = 22.8e-2
print(a, b, c, d)

[output]

10 1000000.0 22.8 0.228

Process finished with exit code 0

```
### 1.1.2. 字符串类型， 布尔类型
```Python
a = 'this'
b = "that"
c = '''those
are 
bad'''

print(a, b, c)

[output]
this that those
are 
bad
```
### 1.1.3. 字符串常用操作：

1. 转义符 和Java 相同 

```Python 
2. # -*- coding: UTF-8 -*- 在文件开头添加可以避免中文乱码  ``
```

3. Python 字符串常用操作
假设实例变量 a 值为字符串 "Hello"，b 变量值为 "Python"：

|操作符 | 描述  | 代码  | 输出|
|------------- | ------------- | ------------- | -------------|
|+ | 字符串连接 | >>>a + b | 'HelloPython'|
|* | 重复输出字符串  | >>>a * 2 | 'HelloHello'|
| []	|通过索引获取字符串中字符	|	>>>a[1]	|	'e'|
| [ : ]|	截取字符串中的一部分	|	>>>a[1:4]	| 'ell'|
|in	| 成员运算符 - 如果字符串中包含给定的字符返回 True	| >>>"H" in a | True |
|not in	| 成员运算符 - 如果字符串中不包含给定的字符返回 True | >>>"M" not in a | True |

4. 格式化输出： 和其他语言的格式化输出类似
```Python
print "My name is %s and weight is %d kg!" % ('Zara', 21)
```

### 1.1.4. 运算符

*： 乘法
/: 除法 ， 浮点数
//: 整除
----------------------------------------------------------------------------------
### 1.2 复杂数据类型
我把Python的数据类型分成简单数据类型和复杂数据类型， 因为在数据挖掘中， 大多数用的是复杂数据类型。所以特此将</br>
其他的数据类型 List, tuple等放到该节来讲。

### 1.2.1 列表

列表是最常用的Python数据类型，它可以作为一个方括号内的逗号分隔值出现。

列表的数据项不需要具有相同的类型

创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可。如下所示：
```Python
list1 = ['physics', 'chemistry', 1997, 2000]
list2 = [1, 2, 3, 4, 5 ]

print(list1[0],list2[5],list1[-1],list2[-3])
[output]  下标0，左边第一个，-1，右边数第一个，
physics 6 2000 5
```
列表可以进行不同的操作：
@@ 与字符串的索引一样，列表索引从0开始。列表可以进行截取、组合等。
```Python
print(list1[2:5])
print(list1[2:])
print(list1[:-1])
[output]
[1997, 2000, 2]
[1997, 2000, 2, 2]
['physics', 'chemistry', 1997, 2000, 2]
```

列表拼接 两种方法：
1.
```Python 
list3=[list1,list2]
print(list3)
[output]
[['physics', 'chemistry', 1997, 2000], [1, 2, 3, 4, 5, 6, 7]]

print(list3[0][1],list3[1][4])
[output] 
chemistry 5
```

@@使用逗号,拼接列表就是生成一个多维的矩阵， 第一个List作为矩阵的第一行， 第n个list作为矩阵的第n行。

2.
```Python
list4=list1+list2
print(list4)
[output]
['physics', 'chemistry', 1997, 2000, 1, 2, 3, 4, 5, 6, 7]
```
@@使用加号，凭借列表就是扩展列表，将两个list合并为一个扩展的list.



list4=list1+list2
print(list4)


