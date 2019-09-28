监督学习

监督学习我们通过花的分类已经进行了了解。 我们再回顾一下： 

通过训练数据集， 训练出模型， 然后通过测试数据集进行验证， 到达足够泛化能力之后， 最后就可以对新数据进行分类。 

所以， 当想要根据给定输入预测某个结果，并且还有输入、输出对的示例时，都应该使用监督学习。
这些输入、输出对构成了训练集， 我们可以通过它来构建机器学习模型。我们的目标是对新数据进行预测。


# 分类与回归

监督学习分为两种，分别叫 <b>分类(classification)</b>  和  <b>回归(regression)</b>

1. 分类问题的目标是 预测类别标签（class label）. 分别有二分类和多分类。二分类就是 是/否。 多分类我们已经接触过例子了。 

2. 回归问题的目标是预测一个连续值，就是预测一个实数。比如预测收入，价格，产量等。

区分分类和回归任务一个简单的方法就是问一个问题： 输出是否具有某种连续性？ 或者输出是否为连续性数值。


# 泛化 、 过拟合 和欠拟合

我们之前了解了 泛化， 就是一个模型对新数据预测的准确率。我们当然需要构建一个预测能力足够高，精确的模型。 

我们再去回忆一下花的例子， 花的特征有4个， 我们极端一点， 如果花的特征只有一个， 比如只有花瓣的宽度一个特征， 就算是训练好的模型准确率够高。 我们能否说这个模型就能预测准确新的数据呢？不太会。

我们再极端一点， 如果我们把花的特征扩大到400个，就说明训练出来的模型就是最佳的呢？ 

一个是太简单， 一个是太复杂， 在机器学习上， 有专门的名称， 分别称为欠拟合和过拟合。 

欠拟合就是一条筋， 见风就是雨。
 而过拟合就是用力过猛， 考虑过多。
 
 所以， 机器学习就是找到两者之间的一个最佳位置。 可以得到最好的泛化性能。 
 
#模型复杂度和数据集的关系

模型复杂度和数据集的大小由密切关系， 数据集中包含的数据点变化范围越大， 在不发生过拟合的前提下，可以使用越复杂的模型。 可以这样说， 更大的数据集可以支持构建更复杂的模型。
需要注意的是， 复制相同的数据点是没有用的。 

#线性回归   

https://www.codecogs.com/eqnedit.php  编写公式的网站

线性回归: 应该是以下公式：
<a href="https://www.codecogs.com/eqnedit.php?latex=$$y=b&plus;a_{0}x_{0}&plus;a_{1}x_{1}&plus;a_{2}x_{2}&plus;a_{3}x_{3}&plus;a_{4}x_{4}&plus;a_{n}x_{n}$$" target="_blank"><img src="https://latex.codecogs.com/gif.latex?$$y=b&plus;a_{0}x_{0}&plus;a_{1}x_{1}&plus;a_{2}x_{2}&plus;a_{3}x_{3}&plus;a_{4}x_{4}&plus;a_{n}x_{n}$$" title="$$y=b+a_{0}x_{0}+a_{1}x_{1}+a_{2}x_{2}+a_{3}x_{3}+a_{4}x_{4}+a_{n}x_{n}$$" /></a>

我们就需要计算出各个特征前面的系数值以及截距来拟合数据。 

```Python

import pandas as pd
import numpy as np
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from matplotlib import pyplot as plt
data = pd.read_csv('files/Advertising.csv', index_col=0)
# 通过pandas的方法，很容易读入一个文档
npp = data.values
# 将读入的dataframe格式数据转换为numpy的矩阵格式
X = npp[:,0:1]
# 截取该矩阵的第一列为输入数据
y = npp[:,3]
# 截取矩阵的最后一列为输出数据
X_train, X_test, y_train, y_test = train_test_split(X,y,random_state=5)
# 进行分类 注意 等号左边变量的顺序。
#print(X_train)
#print("target traing sets\n {}".format(y_train))
model = LinearRegression().fit(X_train,y_train)
# 一句话 ， 进行线性回归模型的训练
print(model.coef_)
print(model.intercept_)
# 该特征的系数和截距
test = np.array([[41.5]])
# 测试数据一定是矩阵格式。np.array
print("result of 41.5 is {}".format(41.5*model.coef_+model.intercept_))
print("result of model is {}".format(model.predict(test)))
# 测试数据的输出结果。
result = model.predict(X)
# 将所有数据点放入模型中进行预测。
plt.plot(X,y,'bo')
plt.plot(X,result, color='red', linewidth=4)
# 在画图中画出点及预测的直线。
plt.show()
```

那我们思考一个问题？  系数是怎么得出来的？？ 

这得从一个基本概念说起。 叫做 “猜谜语”。 专业一点就叫做预测。
那么我们接下来，就要讲一个机器学习中非常重要的概念叫做 <b>梯度</b>。 



