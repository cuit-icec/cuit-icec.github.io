## 引言

在上一节介绍了梯度下降算法，但是我们是从比较简单的例子引入(在上一节我们选择的是一个特征的线性回归方程)，但是在我们解决实际问题的时候，通常我们遇到的变量都是挺多的，比如在解决**波士顿房价问题**的时候，我们遇到的影响房价的特征有13个，那么利用这么多的特征的如何去做一个线性回归呢，去预测出房价是多少呢？这就是这一节讨论的问题。

## 多维特征

下面是一张房价预测的表格，其中可以看出影响房价变化的特征有四个分别是：`Size`, `Number of bedrooms`, `Number of floors`, `Age of home`：

![591785837c95bca369021efa14a8bb1c](../../../_static/images/591785837c95bca369021efa14a8bb1c.png)

像这样一个多维特征，我们就可以写成一个**多维向量**表示的多维特征向量的形式，写成一个 $\mathbf{X}$ 向量：

$$
\mathbf{X}=\left[\begin{array}{c}
1 \\\\
x_{1} \\\\
x_{2} \\\\
x_{3} \\\\
x_{4}
\end{array}\right]
$$

为什么有一个 1，因为在前面说了在具有偏置的情况下，有一个$x_0 = 1$，那个 1 就是 $x_0$。同样的，我们就添加一个偏置，这样就有5个参数 $\theta$，写成一个 $\mathbf{\Theta}$ 向量：

$$
\mathbf{\Theta}=\left[\begin{array}{c}
\theta_0 \\\\
\theta_1 \\\\
\theta_2 \\\\
\theta_3 \\\\
\theta_4
\end{array}\right]
$$

这样的话，我们的**多维线性回归方程**的预测函数，就可以写成：

$$
h_{\theta}(x) = \Theta^{T} X = \left[\begin{array}{cccc}
\theta_0 & \theta_1 & \theta_2 & \theta_3 & \theta_4 \\\\ \end{array}\right] \left[\begin{array}{c} 1 \\\\x_{1} \\\\x_{2} \\\\x_{3} \\\\x_{4}\end{array}\right] \\\\= \theta_{0}+\theta_{1} x_1+\theta_{2} x_2+\theta_{3} x_3+\theta_{4} x_4
$$


## 多变量梯度下降

上一节的例子只有两个 $\theta$：$\theta_0$ 和 $\theta_1$，是这样用梯度下降更新的：


$$
\begin{array}{l}
\theta_{0}:=\theta_{0}-\alpha \frac{1}{m} \sum_{i=1}^{m}\left(h_{\theta}\left(x^{(0)}\right)-y^{(0)}\right) 
\\\\\\\\
\theta_{1}:=\theta_{1}-\alpha \frac{1}{m} \sum_{i=1}^{m}\left(h_{\theta}\left(x^{(1)}\right)-y^{(1)}\right) \cdot x^{(1)}
\end{array}
$$


这个公式是如何来的，这里再提一下：	
$$
\theta_{j}:=\theta_{j}-\alpha \frac{\partial}{\partial \theta_{j}} J\left(\theta_{0}, \theta_{1}\right) \quad(\text { for } j=0 \text { and } j=1)
$$
到这里你估计已经明白在多维特征里面是如何更新参数的了，没错，就是这样：
$$
\begin{array}{l}
\theta_{0}:=\theta_{0}-\alpha \frac{1}{m} \sum_{i=1}^{m}\left(h_{\theta}\left(x^{(0)}\right)-y^{(0)}\right) 
\\\\\\\\
\theta_{1}:=\theta_{1}-\alpha \frac{1}{m} \sum_{i=1}^{m}\left(h_{\theta}\left(x^{(1)}\right)-y^{(1)}\right) \cdot x^{(1)}
\\\\\\\\
\theta_{2}:= \theta_{2}-\alpha \frac{1}{m} \sum_{i=1}^{m}\left(h_{\theta}\left(x^{(2)}\right)-y^{(2)}\right) \cdot x^{(2)}
\\\\\\\\
\theta_{3}:= \theta_{3}-\alpha \frac{1}{m} \sum_{i=1}^{m}\left(h_{\theta}\left(x^{(3)}\right)-y^{(3)}\right) \cdot x^{(3)}
\\\\\\\\
\theta_{4}:= \theta_{4}-\alpha \frac{1}{m} \sum_{i=1}^{m}\left(h_{\theta}\left(x^{(4)}\right)-y^{(4)}\right) \cdot x^{(4)}
\end{array}
$$
好了，到这里你也已经知道，多维特征的线性回归是如何做的了。然后我建议你到这里你就可以去用代码实现一下，用梯度下降来做线性回归（我强烈建议你用python去做这件事）。在实践之前，我还要提一些需要注意的事情(特征缩放，学习率选择)。

## 特征缩放

特征缩放是什么？

> 我们的特征其实往往相差较大，比如说上面的`Size`, 最小有852， 最大有2104；**特征缩放**是指把某一个特征缩小到一个很小的范围：**(-1, 1)**(不一定是这个范围)。比如把852和2104缩小到 (-1, 1)中。

为什么要做特征缩放呢？

> 因为我们使用的是梯度下降来更新参数$\theta$，而梯度下降的步长又是由学习率来决定的，所以如果特征范围比较大，那么要更新到最优解的时候，需要进行多次的迭代，收敛的速度慢（你可以理解为要走的步数多，耗费的时间长）

如何做特征缩放呢？

> 现在用的最多的就是**归一化**，把特征缩小到 -1 到  1 的范围，归一化又有几种方法，我这里介绍最常用的：x = (x - average) / (maximum - minimun)

## 学习率的选择

梯度下降算法收敛所需要的迭代次数根据模型的不同而不同，我们不能提前预知，我们可以绘制迭代次数和损失函数的图表来观测算法在何时趋于收敛：

![cd4e3df45c34f6a8e2bb7cd3a2849e6c](../../../_static/images/cd4e3df45c34f6a8e2bb7cd3a2849e6c.jpg)

也有一些自动测试是否收敛的方法，例如将损失函数的变化值与某个阀值（例如0.001）进行比较，但通常看上面这样的图表更好。

梯度下降算法的每次迭代受到学习率的影响，如果学习率$\alpha$过小，则达到收敛所需的迭代次数会非常高；如果学习率$\alpha$过大，每次迭代可能不会减小损失函数，可能会越过局部最小值导致无法收敛。

这样的学习率需要不断地去根据具体情况去试。

## 总结

多变量的线性回归回归方程采用梯度下降法来做的话，思想和前面的是一样，只是需要多更新一些参数$\theta$。同时实践的时候需要注意，一定要对原始数据做特征缩放，这样做的好处是：能够加快梯度下降的收敛速度；同时要根据实际情况不断地更新学习率，选出最好的学习率。