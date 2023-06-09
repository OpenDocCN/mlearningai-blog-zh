# Pedro Domingos 的文章“关于机器学习需要知道的一些有用的事情”的摘要

> 原文：<https://medium.com/mlearning-ai/summary-of-the-article-a-few-useful-things-to-know-about-machine-learning-by-pedro-domingos-ecf1ef3e6ae9?source=collection_archive---------3----------------------->

![](img/d595945e86949cd0b6768f6b23b5451a.png)

Photo by [Pietro Jeng](https://unsplash.com/@pietrozj?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

这篇文章旨在**总结**Pedro Domingo 文章最重要的方面:**“关于机器学习需要知道的一些有用的事情”。**

主文章的目标是*“交流科学文章中通常没有的关于机器学习的民间知识”*。Pedro 在 ML 方面有丰富的经验，所以我认为这些基于他的经验的建议非常有意义！你可以在这里找到这篇文章——https://homes.cs.washington.edu/~pedrod/papers/cacm12.pdf。

此外，如果你喜欢我的同胞所做的工作(我也是葡萄牙人:)，我推荐他关于机器学习的书—*The Master Algorithm:The Quest for The Ultimate Learning Machine 将如何重塑我们的世界*。这本书解释了不同类型的机器学习算法，是一个很好的机器学习的起点。

我把这篇文章分成 9 个主要的提示:

1.  [学习=表示+评估+优化](http://9e73)
2.  [重要的是归纳——超越训练数据的归纳](http://adf1)
3.  [Oveffiting 有很多面](http://ed3b)
4.  [直觉在高维中失败——维度的诅咒](http://2027)
5.  [理论上的保证并不像它们看起来的那样](http://35a3)
6.  [特色工程是关键](http://391d)
7.  [更多的数据胜过更聪明的算法](http://27da)
8.  [学习多种模式，而不仅仅是一种](http://55d2)
9.  简单并不意味着准确

# 1.学习=表示+评估+优化

通常很难选择最佳的 ML 算法。我们只专注于选择算法，而将其他重要任务抛在脑后。然而，学习由这三个重要方面组成*表现、评估和优化*。因此，**为了成功，我们需要**仔细选择我们将如何*表示*数据，我们将如何*评估*结果，以及我们将如何*找到*最佳算法/参数。

正如 Pedro 所写的，*“机器学习项目中的一些选择甚至可能比学习者的选择更重要”。*

# 2.重要的是概括

主要目标是让**能够超越训练数据**进行归纳。这意味着学习者必须对新的和看不见的数据表现良好。

使用同一组数据来训练和测试模型带来了成功的**假象**。在这种情况下，Pedro 建议*“从一开始就把一些数据放在一边，只用来测试你选择的分类器”*。他还谈到如果我们没有很多数据，我们如何使用交叉验证。

# 3.过度拟合有很多面

每个人都知道过度拟合——用训练数据得到很好的结果，但用新的和看不见的数据得到很差的结果。从这个意义上来说，佩德罗说过度拟合可能会以*“许多形式不会立即显现出来”。*

为了更好地理解过度拟合，Pedro 建议**将泛化误差分为偏差和方差。**正如 Pedro 解释的那样，*“偏差是学习者持续学习相同错误内容的倾向，而方差是学习随机内容而不考虑真实信号的倾向”*。

根据我们选择的模型的表现，我们可以选择基于偏差和方差的算法。例如，线性学习者有很高的偏差，决策树没有很高的偏差，但是有很高的方差。

佩德罗还建议使用*交叉验证和正则化*来对抗过度拟合。他在本节**结尾警告***“陷入适配不足的相反错误很容易避免适配过度”。*

# 4.直觉在高维空间失效

Pedro 以*“过度拟合后，ML 最大的问题是维数灾难”开始这一段。*基本上，当我们使用越来越多的特征时，最大似然算法在更高维度中开始变得非常糟糕。

随着维度的增长，学习数据**变得越来越困难**，因为示例数量和特征数量之间的比率变得非常低。因此，作为一个建议，明智地选择特性并只使用最相关的特性是很重要的。不要给你的学生制造噪音。

# 5.理论上的保证并不像它们看起来那样

这一条很简单——仅仅因为某个算法在理论上取得了好的结果，并不意味着它在实践中也会工作得很好。正如佩德罗所说:“仅仅因为一个学习者有一个理论上的理由并在实践中工作，并不意味着前者是后者的原因。”

# 6.特征工程是关键

在这一部分，Pedro 思考了特征工程的重要性。他解释说，机器学习项目成功的最重要因素是所使用的特征。

对此的解释很简单:*“如果你有许多独立的特征，并且每个特征都与类相关联，那么学习就很容易。另一方面，如果类是一个非常复杂的功能，你可能无法学习它。”*

他还表示，ML 流程**不是**“一次性流程”。这是一个反复的过程，工程师们用新的和不同的特征来测试新的假设，以达到最好的结果。

# 7.更多的数据胜过更聪明的算法

当你的模型不够精确时，你有两个主要的选择:*“设计一个更好的学习算法，或者收集更多的数据(更多的例子，可能还有更多的原始特征】*。佩德罗推荐**第二条路径**。首先，因为获取更多数据通常比构建新算法更快。第二，因为算法从数据中学习，我们拥有的数据越多，算法必须尝试学习的例子就越多。

# 8.学习许多模型，而不仅仅是一个

在这一部分，Pedro 谈论了模型组合的**好处**。他首先说，在*之前，“人们会测试许多模型，然后选择最佳模型”*。但是，一个更好的方法是结合许多不同的模型。这是一个很好的方法，因为我们基本上是将多种算法的优势结合成一种。因此，一种算法的优点解决了另一种算法的缺点。

# 9.简单并不意味着准确

这个很简单:*“给定两个具有相同训练误差的分类器，两个分类器中较简单的可能具有最低的测试误差”。根据经验，我们应该总是选择更简单的算法。正如 Pedro 所解释的，复杂的学习者有更大的假设空间，因此*“一个拥有更大假设空间的学习者尝试更少的假设，比一个在更小空间尝试更多假设的学习者更不容易过度适应。”**

请随意评论您从经验中学到的其他有用技巧:)