# 这一章节主要讲述Python 的 普通语法


## 1. Python 数据类型
### 1.1 基本数据类型
###  1.1.1 基本数据类型
 
 总共有四种： 整数|长整数|浮点数|复数

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

列表的数据项不需要具有相同的类型；

列表的内容可以改变；

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

```Python 
1.----------------------
list3=[list1,list2]
print(list3)
[output]
[['physics', 'chemistry', 1997, 2000], [1, 2, 3, 4, 5, 6, 7]]

print(list3[0][1],list3[1][4])
[output] 
chemistry 5
```

@@使用逗号,拼接列表就是生成一个多维的矩阵， 第一个List作为矩阵的第一行， 第n个list作为矩阵的第n行。


```Python
2.----------------------
list4=list1+list2
print(list4)
[output]
['physics', 'chemistry', 1997, 2000, 1, 2, 3, 4, 5, 6, 7]
```
@@使用加号，凭借列表就是扩展列表，将两个list合并为一个扩展的list.


```Python
list4=list1+list2
print(list4)
```

@@ list.append(); 从末尾添加元素到列表；
@@ list.insert(x,a);从位置x添加元素a到列表；

@@ 元组转换为列表

```Python
tup1 = ('Google', 'Runoob', 1997, 2000);
list1=[12]
list1=list(tup1)
print(list1)
[output]:['Google', 'Runoob', 1997, 2000]
```

###1.2.2 元组

元组和列表的结构相类似， 只是元组的内容不能被修改；

其使用的方法与列表基本相同。

@@@ 初始化一个元组

```Python
tup1 = (50,)
```

###1.2.3 字典

字典是另一种可变容器模型，且可存储任意类型对象。


字典的每个键值(key=>value)对用冒号(:)分割，每个对之间用逗号(,)分割，整个字典包括在花括号({})中 ,格式如下所示：

```Python
dict = {'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}

dict1 = {}  #一个空的字典。
```
这是一个典型的字典定义。

```Python
for i in dict.items():#遍历
    print(i)
    print(list(i))
    
    
[output]:
('Alice', '2341')
['Alice', '2341']
('Beth', '9102')
['Beth', '9102']
('Cecil', '3258')
['Cecil', '3258']
```
注意输出的数据格式； print(i)为输出 tuple格式； print(list(i))为列表格式。

```Python
dict = {}
dict['one'] = "1 - 菜鸟教程"
dict[2]     = "2 - 菜鸟工具"
 
tinydict = {'name': 'runoob','code':1, 'site': 'www.runoob.com'}
 
 
print (dict['one'])       # 输出键为 'one' 的值
print (dict[2])           # 输出键为 2 的值
print (tinydict)          # 输出完整的字典
print (tinydict.keys())   # 输出所有键
print (tinydict.values()) # 输出所有值


[output]
1 - 菜鸟教程
2 - 菜鸟工具
{'name': 'runoob', 'code': 1, 'site': 'www.runoob.com'}
dict_keys(['name', 'code', 'site'])
dict_values(['runoob', 1, 'www.runoob.com'])
```
字典可以输出指定key的value
字典可以输出完整的key-value值
字典可以遍历所有的key和 value.

@@ 注意的是字典是无序的。
@@ 字典的Key是唯一的。

字典的操作

```Python

dict0 = dict()  # 传一个空字典
print('dict0:', dict0)
 
dict1 = dict({'three': 3, 'four': 4})  # 传一个字典
print('dict1:', dict1)
 
dict2 = dict(five=5, six=6)  # 传关键字
print('dict2:', dict2)
 
dict3 = dict([('seven', 7), ('eight', 8)])  # 传一个包含一个或多个元祖的列表@@关键的关键
print('dict3:', dict3)
 
dict5 = dict(zip(['eleven', 'twelve'], [11, 12]))  # 传一个zip()函数
print('dict5:', dict5)

[output]
dict0: {}
dict1: {'four': 4, 'three': 3}
dict2: {'five': 5, 'six': 6}
dict3: {'seven': 7, 'eight': 8}
dict5: {'twelve': 12, 'eleven': 11}
```
添加元素：

```Python
dict1['def']=4
print(dict1)

```
遍历元素并搜索相应的值删除

```Python
d = {'a':1, 'b':0, 'c':1, 'd':0}
keys = list(d.keys())  # 注意这里需要将字典的key改成list做遍历， 不然删除后，遍历条件会更改。
print(keys)
for key in keys:    
   if((d[key])<1):
    del d[key]
print(d)

```
### 1.2.4 集合
集合（set）是一个无序的不重复元素序列。可以看成是一个没有value的字典

```Python

abc = set() # 定义一个空集合

abc.add(6)
abc.add("kid")
print(abc)
[output]
{6,"abc"}

abc={1,2,3,4,5,6,7,8,9}
bcd=set('123456789')
print(abc)# 注意区别bcd
print(bcd)# 注意区别abc
```
@@@ 如果将相同的value添加到集合中， 那么该集合不会增加。 


```Python
a = {x for x in 'abracadabra' }
print(a)
b = {x for x in 'abracadabra' if x not in 'abc'}
print(b)

[output]
{'a', 'b', 'r', 'd', 'c'}
{'r', 'd'}
```

## 2. Python 程序结构

@@ 程序结构注意缩进！！！

### 2.1 判断

if else 和Java 相同

### 2.2 循环

```Python
languages = ["C", "C++", "Perl", "Python"] 
for x in languages:
	print(x);
```

```Python
for x in range(1, 11):
print(x)
[output] 1,2,3,4,5,6,7,8,9,10

```

```Python
for x in range(1, 11):
...     print('{0:2d} {1:3d} {2:4d}'.format(x, x*x, x*x*x))
...
 1   1    1
 2   4    8
 3   9   27
 4  16   64
 5  25  125
 6  36  216
 7  49  343
 8  64  512
 9  81  729
10 100 1000
```



## 3. 函数

### 3.1 无参函数

```Python
def hello():
    print("hello world")
```

### 3.2 带参数函数

```Python
def area(width, height):
    return width * height
 
def print_welcome(name):
    print("Welcome", name)
 
print_welcome("Runoob")
w = 4
h = 5
print("width =", w, " height =", h, " area =", area(w, h))
```

### 3.3 Python 函数需要注意的地方

@@@ 不可变参数

```Python
def ChangeInt( a ):
    a = 10
 
b = 2
ChangeInt(b)
print( b ) # 结果是 2
```
解释上述代码是， 对象2， 一个变量b指向该对象。 当a最为参数被b调用的时候。 a,b同时指向2, 在
函数中执行 a=10, 表示变量a又指向对象10； 所以 a=10, b=2

@@@ 可变参数

```Python

def changeme( mylist ):
   "修改传入的列表"
   mylist.append([1,2,3,4])
   print ("函数内取值: ", mylist)
   return

mylist = [10,20,30]
changeme( mylist )
print ("函数外取值: ", mylist)
```

@@@ 默认参数

```Python
def printinfo( name, age = 35 ):
   "打印任何传入的字符串"
   print ("名字: ", name)
   print ("年龄: ", age)
   return

printinfo( age=50, name="runoob" )
print ("------------------------")
printinfo( name="runoob" )

[output]
名字:  runoob
年龄:  50
------------------------
名字:  runoob
年龄:  35
```

@@@ 不定长参数函数

def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vartuple)
 
printinfo( 70, 60, 50 )

```

## 4.导入 
### 4.1 import
创建一个fibo.py的文件， 该文件里有两个函数：fib2(n)；fib(n)； 
那么：import fibo之后就用下面的代码用该文件的两个函数：
fibo.fib2(2); fibo.fib(2)

### 4.2from fibo import fib, fib2

fib(2); fib2(2);   @@ 注意和4.1 的区别

from modname import *； 把该模块的所有函数都导入。

## 5.输入和输出
### 5.1 输出
print('{0} 和 {1}'.format('Google', 'Runoob'))
Google 和 Runoob

print('{name}网址： {site}'.format(name='菜鸟教程',site='www.runoob.com'))
菜鸟教程网址： www.runoob.com

### 5.2 输入

str = input("请输入：");
print ("你输入的内容是: ", str)

### 5.3 文件读

```Python
f = open("/tmp/foo.txt", "r")# 打开一个文件
for line in f:
    print(line, end='')
f.close()# 关闭打开的文件
```

### 5.3 文件写

```Python

f = open("/tmp/foo1.txt", "w")# 打开一个文件
value = ('www.runoob.com', 14)# 当写入内容不是字符串格式， 需要将其转换为字符串
s = str(value)
f.write(s)
f.close()# 关闭打开的文件
```



