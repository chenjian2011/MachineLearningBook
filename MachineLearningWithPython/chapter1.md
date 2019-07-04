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
# 这里的大括号 就是格式输出的占位符。 将格式输出占位
```