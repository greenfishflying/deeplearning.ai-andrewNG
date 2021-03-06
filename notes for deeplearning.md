notes for deeplearning
====

1.loss function（损失函数）：
----

一个测试数据输入网络后，输出结果与真实值的差距

2.cost function(代价函数)：
----

整个测试集输入网络后，每一g个测试函数输出的损失函数的平均值

![](https://pic2.zhimg.com/80/v2-5ea83a72fd6d4bfe60e822898291f821_hd.png)


3.检查矩阵维度：
----

![](./img/dplw4.png)
![](./img/dplw42.png)


W[L]=(n(L),n(L-1))

b[L]=(n(L),1)

dW[L]=(n(L),n(L-1))

db[L]=(n(L),1)

Z[L]=(n(L),m)   (m为样本个数)

dZ[L]=(n(L),m)

训练集
----

这个是最好理解的，用来训练模型内参数的数据集，Classfier直接根据训练集来调整自身获得更好的分类效果



验证集   
----

用于在训练过程中检验模型的状态，收敛情况。验证集通常用于调整超参数，根据几组模型验证集上的表现决定哪组超参数拥有最好的性能。   

同时验证集在训练过程中还可以用来监控模型是否发生过拟合，一般来说验证集表现稳定后，若继续训练，训练集表现还会继续上升，但是验证集会出现不升反降的情况，这样一般就发生了过拟合。所以验证集也用来判断何时停止训练

测试集
----

测试集用来评价模型泛化能力，即之前模型使用验证集确定了超参数，使用训练集调整了参数，最后使用一个从没有见过的数据集来判断这个模型是否Work。

作者：Ph0en1x
链接：https://zhuanlan.zhihu.com/p/35394638
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。


偏差、方差
----
对于下图中两个类别分类边界的分割： 

![](https://img-blog.csdn.net/20170928161736059?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvS29hbGFfVHJlZQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

从图中我们可以看出，在欠拟合（underfitting）的情况下，出现高偏差（high bias）的情况；

在过拟合（overfitting）的情况下，出现高方差（high variance）的情况。

在bias-variance tradeoff 的角度来讲，我们利用训练集对模型进行训练就是为了使得模型在train集上使 bias 最小化，避免出现underfitting的情况；

解决办法

![](https://img-blog.csdn.net/20170928171621914?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvS29hbGFfVHJlZQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

高偏差（欠拟合）--->更大的网络/更长时间的训练/（换网络）

高方差（欠拟合）--->更多数据/正则化

正则化：
----

简单来讲，

作用：防止过拟合

当lamda变得很大，部分权重会变得很小，在激活函数中不具备非线性功能，相当于被屏蔽掉

Dropout 正则化:
----
Dropout（随机失活）就是在神经网络的Dropout层，为每个神经元结点设置一个随机消除的概率，对于保留下来的神经元，我们得到一个节点较少，规模较小的网络进行训练。

![](https://img-blog.csdn.net/20170928214708004?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvS29hbGFfVHJlZQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

超参数调节:
----

最重要：

α:学习率

其次：

β：动量项

mini-bantch size：小规模样本内含数量

隐藏单元数量

再次：

学习率衰减

网络层数

最次：
Adam算法参数

![](./img/w2m1.npg.png)

