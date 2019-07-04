```Python
from sklearn.datasets import load_iris

iris_dataset = load_iris()

#print("keys of iris_dataset: \n{}".format(iris_dataset.keys()))
# output dict_keys(['data', 'target', 'target_names', 'DESCR', 'feature_names'])

#print("Target names: \n{}".format(iris_dataset['target_names']))
# 分类名
#print("data names: \n{}".format(iris_dataset['data']))
#具体数值
#print("feature names: \n{}".format(iris_dataset['feature_names']))
#每个案例个体包含的属性名
#print("Target names: \n{}".format(iris_dataset['target']))
#分类值  就是 data属于哪一类的值。0,1,2

# 可以看出， 数组中包含了150朵不同花的测量数据。
# 用机器学习的专业术语来说， 我们这里有150个样本，每个样本有3个特征。
# 我们的这个数据就 样本数 x 特征数 形成了一个形状。 在scikit-learn 中数据始终遵循这个约定。

print("first five data:\n{}--".format(iris_dataset['data'][:5]))
# 这里的大括号{} 就是格式输出的占位符。 将格式输出占位
```

写到这里， 我们已经基本上了解我们需要分析的这个数据集了。 这个数据集包含了150个样本， 每个样本有4个特征； 这150个样本总共被分成了3个类别。

那么， 如果我们接收了一个新的样本， 能不能够构建一个系统， 让机器能够自动识别分类该样本呢？
这， 就是<b>机器学习</b>所可以完成的功能。 

现在， 我们想要利用这些数据构建一个机器学习模型，用于预测新策略的花的品种（分类）。在讲模型应用到新的测量数据之前，我们需要知道我们的这个模型是否有效，是否能相信这个预测结果么？

让我们回顾 “学习”，在驾校操场中熟练掌握的驾驶技巧是否证明能在真实道路上开车？ 为什么？
这个和我们的机器学习模型中的数据有什么关联之处？

1. 驾驶技术学习： 因为在驾校操场上的各种路况，已经很熟悉并且不变，训练熟练之后肯定可以完成。 但是在真实道路上， 熟悉的各种路况可能会变得不熟悉，很多路况可能是从来没碰到过的。所以在驾校操场上的100分并不能真实代表你的驾驶能力。

2. 机器学习： 如果利用数据集学习好了之后，再用该数据集进行测试， 是不能保证该模型的正确性。

总而言之，我们的模型训练好之后，会一直记住整个训练集（驾校操场），所以该模型无法告诉我们对于新数据的预测能力。也就是该模型的 泛化能力（广泛数据的化解能力）我们无法得知。


我们想要利用这些数据构建一个机器学习模型，我们就需要用新数据来评估模型的性能。 新数据是指模型之前没有见过的数据，而我们有这些新数据的标签。

通常的做法，是将收集好的数据， 这里是150朵花，分成两部分，一部分数据用于构建机器学习模型，叫做<b>训练数据 (training data)</b>或者 <b>训练集 (training set)</b>。其余的数据用来评估模型性能，叫做 <b>测试数据(test data)、测试集(test set)</b>。

scikit-learn 中的train_test_split函数可以打乱数据集并进行拆分。这个函数将75%作为训练集，25%作为测试集。经验来说这种比例分配是最好的。

scikit-learn 中的数据通常用大写的X来表示，标签用小写的 y表示。 因为数学公式f(x)=y. 
x 是输入，通过函数计算得到输出y. 用大写的X来表示， 因为一般情况，数据集是一个二维数组，也就是我们说的矩阵，用小写y 因为输出目标为一个向量（一维数组），这也是数学的约定。

```Python
X_train,X_test,y_train,y_test = train_test_split(iris_dataset['data'],
                                                 iris_dataset['target'],
                                                 random_state=0)
# train_test_split函数的参数： 1. mxn 矩阵， 2. m向量， 3. 随机种子数；
# 就会生成四个变量 X_train,X_test,y_train,y_test。
```
