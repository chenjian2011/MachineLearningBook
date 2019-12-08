#scikit 之  回归。

## 最小二乘法

定义：y= w1(x1)+w2(x2)+w3(x3)+w4

X(1~n) 为特征向量，我们定义为：coef_ 

w4： 我们定义为截距： intecept_

y:为输出值。  

scikit-learn可以很容易将该模型展示给我们，只需要下列几行代码：


```
from sklearn import linear_model
reg = linear_model.LinearRegression()
#线性回归
reg.fit ([[60], [75], [110],[140]], [336,419, 630,785])

print(reg.intercept_)
print(reg.coef_)
```

岭回归

```
from sklearn import linear_model
reg = linear_model.Ridge
reg.fit ([[60], [75], [110],[140]], [336, 419, 630,785])
```

SGDRegressor回归（大批量数据）

```
from sklearn import linear_model
reg = linear_model.SGDRegressor()

X = [[60], [75], [110], [140]]
y = [336, 419, 630, 785]
reg.fit(X,y)
```


