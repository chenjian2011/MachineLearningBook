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
# 用机器学习的专业术语来说， 我们这里有150个样本，每个样本有4个特征。
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

print("训练数据集：{}".format(X_train.shape))
print("训练标签数据集：{}".format(y_train.shape))
print("测试数据集：{}".format(X_test.shape))
print("测试标签数据集：{}".format(y_test.shape))

[output]:
训练数据集：(112, 4)
训练标签数据集：(112,)
测试数据集：(38, 4)
测试标签数据集：(38,)

```

到了这一步， 我们的数据已经分别整理出来了， 包括训练数据集和测试数据集。 
分别保存到四个变量中：X_train,X_test,y_train,y_test。

我们可以开始使用分类算法进行训练数据了：

```Python
knn = KNeighborsClassifier(n_neighbors=1)
#判断离点最近的一个邻居属于哪个类别。
knn.fit(X_train,y_train)
# 两行代码， 训练好了。

new_data = np.array([[5, 2.9, 1, 0.2]])
p = knn.predict(new_data)
print(p)
print("Target names: \n{}".format(iris_dataset['target_names'][p]))
# 这里 用np.array的二维数组来进行测试参数数组的建立
# iris_dataset['target_names']还记得么？ 是一个一维组数['setosa' 'versicolor' 'virginica']。 
获得该数组的第一个元素应该就是 iris_dataset['target_name']这个数组下标为0的元素，即：
iris_dataset['target_name'][0]
```
就这么简单， 你看， 我们已经使用了机器学习， 把150个数据集的数据进行KNN的分类训练。 训练出来的模型knn就可以对新数据进行分类了。 

那么， 有没有同学怀疑， 凭什么这个分类结果就是对的呢？ 也就是说， 我们对于knn的这个模型的分类结果能否相信呢？ 
scikit-learn 已经帮我们想好了， 它可以计算knn的精度来衡量模型的。

```Python
y_pred = knn.predict(X_test) # 对测试数据集的测试
print("测试数据集的模型测试：\n{}".format(y_pred))
print("测试标签数据集：\n{}".format(y_test))

# 判断这两个数组的相同率有多少
print("准确率：\n{:.2f}".format(np.mean(y_pred == y_test)))

print("准确率：\n{:.2f}".format(knn.score(X_test,y_test)))
```

对于这个模型，准确率的精度为0.97。 也就是说我们的这个knn模型， 预测的准确率达到97%。 

# 章节总结
我们首先介绍了一个任务，就是通过花的不同特征来预测其品种。 在构建模型的时候， 我们用到了标注过的测试数据集，这些数据集已经给出了花的正确品种。 这是一个分类问题。 
可能的品种被成为 <b>类别(class)</b>  ， 每朵花的品种被称为它的<b>标签(label)</b>.

这些花的数据集包含了两个Numpy数组： 一个包含花的特征，在scikit-learn中通常表示X,一个包含正确的输出 （标签）， 通常表示y；数组X是特征的二维数组，每个数据点对应一行，每列对应一个特征值。数组y是个一维数组，里面包含一个类别标签，0~2的整数。

我们通过scikit-learn 的train_test_split函数将数据集随机7/3分成训练数据集和测试数据集，训练数据集构建模型， 测试数据集用于评估模型的泛化能力。

我们选择了k近邻分类算法，根据新点距离最近的邻居来预测。 该算法在KNeighborsClassifier类中实现，利用fit方法来构建模型，传入参数为X_train, y_train。 训练结束之后， 我们可以用score方法， X_test来测试y_test， 得到是否有足够的泛化能力。
最后得出结果为97%. 算是比较满意的一个精度。

