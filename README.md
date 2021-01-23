# SVM-python-
This is a simple implement of SVM

### 写在前面
博主现在在学《统计学习方法》这本书，折腾支持向量机也有半个月多了，之前一直想要把支持向量机搞懂，所以就想集中一段时间来学支持向量机，但是因为懒惰，断断续续地磨了很久。这两天终于实现了支持向量机，这里想把代码分享给大家。
代码主要参考了两个网友的实现，这里给出参考的网页链接：1）[参考代码1](https://www.pkudodo.com/2018/12/16/1-8/)；2）[参考代码2](https://www.cnblogs.com/further-further-further/p/9596898.html)。
参考的两个代码都有比较模糊的地方。而我的代码也没好到哪里去，但是代码中每个地方对应于什么内容都有注释，相对会比较清晰些。我也给出了两个小的数据集用于训练，数据集的特征都是2维的，所以训练完后可以画出决策边界，就没用测试集了，因为直接看决策边界的效果也比较清楚。其中第1个训练集是来自于是「参考代码2」的，第2个训练集是吴恩达机器学习作业6中的。我会上传到资源，供大家下载测试。
对于支持向量机的内容，我这里不做详细的讲解，因为网上也有挺多不错的讲解了，我这里给出我自己的学习SVM用到的资料：
1）《统计学习方法》
2）[零基础学SVM](https://zhuanlan.zhihu.com/p/24638007)
3）[支持向量机(SVM)原理剖析及实现](https://www.pkudodo.com/2018/12/16/1-8/)
4）[李航统计学习之SVM支持向量机+SMO算法数学推导](https://www.bilibili.com/video/BV1S741117Pw
)
课本上有些地方没有说清楚，所以另外找些学习资料还是很有必要的，但是我还是有些地方不明白呀。刚开始学支持向量机的同学，强烈建议先看「零基础学SVM」，这里面讲清楚了对偶问题。然后软间隔和核函数那里，可以看最后两个资料，最后的那个视频资料我觉得很不错，跟着视频公式推下来，多看几遍就差不多了。个人觉得支持向量机还是有一定难度的，需要花点时间来学，反正我是真的花了挺多时间的。
### 代码思路说明
这个代码我是按照《统计学习方法》中SMO算法的描述来实现的，代码的整个框架其实就是两个$\alpha$变量的选择。
关于第一个$\alpha$的选择，书中说首先遍历所有满足条件$0<\alpha_i<C$的样本点，即在间隔边界上的支持向量点，检验它们是否满足KKT条件。如果这些样本点都满足KKT条件， 那么遍历整个训练集，检验它们是否满足KKT条件。我没有严格按照这个步骤来，初始时，因为所有的$\alpha$都为$0$，所以首先是直接遍历整个训练集来选出第一个$\alpha$，这样每个样本都可以成为第一个$\alpha$，都有机会进行更新。这样运行一轮后，有些$\alpha$就已经被更新了，不再为0，那么下一轮就可以从训练集中选出所有满足$0<\alpha_i<C$的样本（支持向量），然后遍历这些样本，让每个支持向量样本的$\alpha$都作为第一个$\alpha$变量继续进行更新。每一轮的遍历都会记录参数的更改次数，如果遍历支持向量样本时，修改次数为$0$，说明所有的支持向量样本点都满足KKT条件，那么后面就转为整个训练集的遍历。如果遍历整个数据集修改次数为$0$，说明收敛了，结束训练。如果不为$0$，说明有参数更新，下一轮就转为遍历支持向量样本。所以$\alpha_1$的选择是在整个训练集和支持向量集的交替遍历中进行，具体见下面的代码。这个思路是「参考代码2」的。
关于第二个$\alpha$的选择，书中说是希望选择的第二个$\alpha$能使$\alpha_2$有足够大变化，即使$\vert E_1-E_2 \vert$最大。那么这里我就直接把$E_1$与所有样本的$E$值作差，然后选出使$\vert E_1-E \vert$最大的样本作为第2个$\alpha$变量。之后，就是对$\alpha_1$、$\alpha_2$、$E_1$和$E_2$等的更新了。直接看代码可能思路会更清晰些，如果有不太明白的，直接评论里问。
参数的话我没调，核函数的$\sigma$设为0.1，$C$设为200。挺多代码都这么设，画出的决策边界结果也还可以。
### 训练结果图
##### dataset_1
原始数据集分布
![dataset_1_数据原始分布](https://img-blog.csdnimg.cn/2021012310433173.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x5bjU4MzI1MDA=,size_16,color_FFFFFF,t_70)
决策边界
![dataset_1_决策边界](https://img-blog.csdnimg.cn/2021012310433132.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x5bjU4MzI1MDA=,size_16,color_FFFFFF,t_70)
##### dataset_2
原始数据集分布
![dataset_2_数据原始分布](https://img-blog.csdnimg.cn/2021012310433192.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x5bjU4MzI1MDA=,size_16,color_FFFFFF,t_70)
决策边界
![dataset_2_决策边界](https://img-blog.csdnimg.cn/2021012310433128.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x5bjU4MzI1MDA=,size_16,color_FFFFFF,t_70)

