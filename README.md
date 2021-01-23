# SVM-python-
This is a simple implement of SVM

### 写在前面
现在在学《统计学习方法》这本书，折腾支持向量机也有半个月多了，之前一直想要把支持向量机搞懂，所以就想集中一段时间来学支持向量机，但是因为懒惰，断断续续地磨了很久。这两天终于实现了支持向量机，这里想把代码分享给大家。  
代码主要参考了两个网友的实现，这里给出参考的网页链接：1）[参考代码1](https://www.pkudodo.com/2018/12/16/1-8/)；2）[参考代码2](https://www.cnblogs.com/further-further-further/p/9596898.html)。  
参考的两个代码都有比较模糊的地方。而我的代码也没好到哪里去，但是代码中每个地方对应于什么内容都有注释，相对会比较清晰些。我也给出了两个小的数据集用于训练，数据集的特征都是2维的，所以训练完后可以画出决策边界，就没用测试集了，因为直接看决策边界的效果也比较清楚。其中第1个训练集是来自于是「参考代码2」的，第2个训练集是吴恩达机器学习作业6中的。我会上传到资源，供大家下载测试。  
对于支持向量机的内容，我这里不做详细的讲解，因为网上也有挺多不错的讲解了，我这里给出我自己的学习SVM用到的资料：  
1）《统计学习方法》  
2）[零基础学SVM](https://zhuanlan.zhihu.com/p/24638007)  
3）[支持向量机(SVM)原理剖析及实现](https://www.pkudodo.com/2018/12/16/1-8/)  
4）[李航统计学习之SVM支持向量机+SMO算法数学推导](https://www.bilibili.com/video/BV1S741117Pw)  
课本上有些地方没有说清楚，所以另外找些学习资料还是很有必要的，但是我还是有些地方不明白呀。刚开始学支持向量机的同学，强烈建议先看「零基础学SVM」，这里面讲清楚了对偶问题。然后软间隔和核函数那里，可以看最后两个资料，最后的那个视频资料我觉得很不错，跟着视频公式推下来，多看几遍就差不多了。个人觉得支持向量机还是有一定难度的，需要花点时间来学，反正我是真的花了挺多时间的。  
### 训练结果图
#### dataset_1
原始数据集分布  
![dataset_1_数据原始分布](https://github.com/Ling6/SVM-python-/blob/main/resultImg/dataset_1_%E5%8E%9F%E5%A7%8B%E6%95%B0%E6%8D%AE%E5%88%86%E5%B8%83.png)  
决策边界  
![dataset_1_决策边界](https://github.com/Ling6/SVM-python-/blob/main/resultImg/dataset_1_%E5%86%B3%E7%AD%96%E8%BE%B9%E7%95%8C.png,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x5bjU4MzI1MDA=,size_16,color_FFFFFF,t_70)  
#### dataset_2
原始数据集分布  
![dataset_2_数据原始分布](https://github.com/Ling6/SVM-python-/blob/main/resultImg/dataset_2_%E5%8E%9F%E5%A7%8B%E6%95%B0%E6%8D%AE%E5%88%86%E5%B8%83.png,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x5bjU4MzI1MDA=,size_16,color_FFFFFF,t_70)  
决策边界  
![dataset_2_决策边界](https://github.com/Ling6/SVM-python-/blob/main/resultImg/dataset_2_%E5%86%B3%E7%AD%96%E8%BE%B9%E7%95%8C.png,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2x5bjU4MzI1MDA=,size_16,color_FFFFFF,t_70)

