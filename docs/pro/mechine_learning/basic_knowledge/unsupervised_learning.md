## 引入

理解了上面的监督学习的话，无监督学习是很好理解的，无非就是不给机器正确的答案，让学习算法自己去领悟。

下面我还是按照习惯给出学术上面对于无监督学习的定义：

> **Unsupervised learning** (UL) is a type of algorithm that learns patterns from untagged data. The hope is that through mimicry, the machine is forced to build a compact internal representation of its world. In contrast to [Supervised Learning](https://en.wikipedia.org/wiki/Supervised_learning) (SL) where data is tagged by a human

下面我还是通过一个例子向你说明机器学习在无监督学习下是如何运作的。

## 举例

假设有两堆样本（A是蓝色圆圈，B是红色叉叉）：

<img src="..\..\..\_static\images\0c93b5efd5fd5601ed475d2c8a0e6dcd.png" alt="20210205201229" style="zoom:100%;" />

我们要将他分类，那么监督学习和非监督学习的工作原理的区别是怎样的？

**监督学习是这样的**：

<img src="..\..\..\_static\images\20210205201229.png" alt="20210205201229" style="zoom:50%;" />

监督学习是找到这样一条分类线，在分类线以下的数据是A, 分类线以上的数据是B。

**但是无监督学习是这样的**：

<img src="..\..\..\_static\images\94f0b1d26de3923fc4ae934ec05c66ab.png" alt="20210205201229" style="zoom:100%;" />

找到两个圈去分类这两个数据，因为他认为这两个数据具有不同的特征表现。

在无监督学习中，我们已知的数据。看上去有点不一样，不同于监督学习的数据的样子，即无监督学习中没有任何的标签或者是有相同的标签或者就是没标签。所以我们已知数据集，却不知如何处理，也未告知每个数据点是什么。别的都不知道，就是一个数据集。你能从数据中找到某种结构吗？针对数据集，无监督学习就能判断出数据有两个不同的聚集簇。这是一个，那是另一个，二者不同。是的，无监督学习算法可能会把这些数据分成两个不同的簇。所以叫做**聚类算法**（后面会单独提到）。

## 总结

**All in all**，无监督学习，就是一种无数据矫正的学习方法，过程就是让学习算法自己去数据中提取某个特征。目前无监督学习的代表算法：聚类算法。这个算法在天文数据分析， 基因工程用的十分广泛。但是目前大多学习算法都是基于监督学习去做的，因为实验表明，监督学习的效果是好于无监督学习的。