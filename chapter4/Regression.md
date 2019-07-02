# 逻辑回归


```python

from sklearn.datasets import load_breast_cancer
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression

 逻辑回归的算法  newfile1.py
 
**#导入数据
breast_cancer = load_breast_cancer()
samples = breast_cancer.data   #  【样本】(或者也叫【示例】)
label = breast_cancer.target   #  【标记】

*#split data

*# 将矩阵随机划分成训练集和测试集, test_size表示测试集的比例(即训练集：测试集=7:3)
sample_train, sample_test, label_train, label_test = train_test_split(samples, label, test_size=0.3)

*# use classifier
classifier = LogisticRegression()
classifier.fit(sample_train, label_train)  # 训练分类模型(Fit the model according to the given training data)

count = 0
Length = len(label_test)

for i in range(Length):
    if classifier.predict(sample_test)[i] != label_test[i]:  # 预测测试样本
        count += 1

print(count)  # 打印预测错误的样本数
print((Length-count)/Length)  # 打印准确率
```

