# 这一章节主要讲述Python 的 普通语法


## Python 数据类型
#####  1. Python 中， 数据类型总共有4种：
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
##### 2. 字符串类型， 布尔类型
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

###### 字符串常用操作：

1. 转义符 和Java 相同 \' \"" 等。

2. # -*- coding: UTF-8 -*- 在文件开头添加可以避免中文乱码

---------
假设实例变量 a 值为字符串 "Hello"，b 变量值为 "Python"：
+|字符串连接| >>>a + b|'HelloPython'
* |重复输出字符串  |>>>a * 2 |'HelloHello'
[]	通过索引获取字符串中字符		>>>a[1]		'e'
[ : ]	截取字符串中的一部分		>>>a[1:4]	'ell'
in	成员运算符 - 如果字符串中包含给定的字符返回 True	>>>"H" in a True
not in	成员运算符 - 如果字符串中不包含给定的字符返回 True >>>"M" not in a True



