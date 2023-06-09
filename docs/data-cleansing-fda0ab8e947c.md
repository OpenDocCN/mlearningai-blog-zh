# 数据清理

> 原文：<https://medium.com/mlearning-ai/data-cleansing-fda0ab8e947c?source=collection_archive---------10----------------------->

![](img/cbe0da81abf01a9bb5cc2a3dc6468a78.png)

Image is created by Divyojyoti Ghosh(me) on [www.canva.com](http://www.canva.com) using different elements available for making designs.

数据清洗是从实际数据中为分析准备高质量的数据，而实际数据通常是低质量的。这里的低质量数据是指具有各种不规则性的数据，如缺失值、异常值、噪声等。一般来说，数据清理和准备大约占数据工程总时间的 80%。

数据挖掘算法通常假设输入数据没有不规则性，并且它产生与所提供的数据相关的结果，因此，准备好高质量的数据以使数据挖掘算法工作良好并产生有用的模式和输出是非常重要的。此外，数据清理生成的数据集小于真实数据集，这提高了数据挖掘算法的效率。

数据清理包括四个操作—

1.  抽样
2.  处理异常值
3.  处理缺失值
4.  平衡数据集

# 抽样

抽样是从全部数据中选择一部分数据。总数据也称为*人口。*使用*种群有两个基本问题，*第一个问题是在许多情况下无法获得全部数据，例如，如果我们正在研究植物的叶子，就不可能收集地球上所有可用叶子的数据。第二个问题是，即使有可能收集许多情况下的全部数据，例如交易数据，计算也变得非常困难，因为对于算法和运行该算法的系统来说，这是太大的负荷。

抽样的基本思想是选择考虑总体最大可变性的数据子集。有几种类型的采样技术用于对整个数据进行采样—

1.简单随机抽样——这项技术背后的主要思想是减少选择偏差。在这种情况下，记录是随机选择的，数据集中的每条记录都有同等的机会被选中。

2.系统抽样—在这种技术中，随机选择第一个记录，然后每隔一段固定时间选择一个记录作为样本的一部分。

3.分层随机抽样—在这种技术中，根据记录的特征将整个群体分为子群体，然后从每个子群体中随机选择记录。子组的比例保持与原始数据集中的比例相同。假设总人口有 100 人，其中 80 人就业，20 人失业。如果样本的总人数需要为 10 人，那么将从就业群体中随机选择 8 人，从失业群体中随机选择 2 人。

# 极端值

离群值是那些其值与其余记录有很大不同的记录。这些异常值通常是由于数据收集过程中的异常计算或用于计算的仪器中的一些错误造成的，或者有时它们确实是例外情况。离群值应该从数据中删除，因为它们会产生错误的模式，或者即使离群值是真正的例外情况，它们也会产生无法应用于一般数据的模式。

有几种方法可以检测异常值。我们可以使用**箱线图**来检测异常值，如果我们使用箱线图来可视化数据集，胡须上方或胡须下方的数据可以被视为异常值。我们还可以使用**四分位数间距**方法来检测异常值，在该方法中，我们通过从第三个四分位数值(第 75 个百分点)中减去第一个四分位数值(第 25 个百分点)来计算四分位数间距(IQR)。然后我们用公式 ***第 1 四分位数值- 1.5* x *IQR*** 计算下限，用 ***第 3 四分位数值+1.5* x *IQR 计算上限。*** 超出此限值的值被视为异常值。有几种模型可用于发现异常值，如隔离林、局部异常值因子等。

# 缺少值

在数据集中，可能存在某些属性值缺失的记录，这些值称为缺失值。这些值可能由于不同的原因而丢失，对这些丢失值的处理取决于丢失的原因。

缺失值可以分为三种类型—

1.  完全随机失踪(MCAR)
2.  随机失踪(三月)
3.  非随机缺失(MNAR)

**完全随机缺失(MCAR)**-当数据完全随机缺失时，这意味着缺失背后的原因既不是其值也不是该记录的任何其他属性值。数据丢失是因为人为错误或设备错误，或者可能是人生病了，或者可能是一些技术错误。

在这种情况下，数据丢失的概率对于所有记录都是相同的，换句话说，由于这个原因，任何值都可能丢失。原因与任何价值或价值本身都没有关系。

**随机缺失(MAR)** —当特定属性的值缺失的原因是另一个属性的值时，这些缺失的值被视为 MAR 类型。例如，大多数属于农村地区的人缺少“年龄”属性值，因为在农村地区，许多人不识字，他们不知道自己的出生日期。在这种情况下，我们可以预测原因，但无法了解丢失的值。

**非随机缺失(MNAR)** —当某个值非随机缺失时，这意味着该值缺失背后的原因是该值本身。比如收入低的人，收入就不太可能进入。在这种情况下，平均收入总是偏向一个更高的数字。

有两种方法可以处理缺失值—

1.  **删除** —如果缺少一个或多个属性值的记录数量减少，可以选择删除这些记录。但是如果数据不是 MCAR，这种技术会引入偏差。
2.  **插补** —这种技术是猜测缺失的值，并用它替换。有不同的方法，例如用该列中值的**平均值**或**中值**替换缺失值，如果该列是数字类型，并且如果该列是分类的，则可以使用**模式**替换该值。最近邻算法也可以用于插补，或者可以创建一个模型来预测缺失数据的值。

## 平衡

现实世界的数据集可能比其他数据集包含更多特定类或组的数据。一些组在数据集中的条目数量可能非常少。分类算法对于数据集可能具有非常好的准确性，即使它完全忽略了特定的类，因为该类具有非常少的条目。例如，在一个数据集中有 90 个就业人员条目和 10 个失业人员条目，在这种情况下，即使算法将所有 10 个失业人员分类为就业，它也可以达到 90%的准确率。我们需要平衡数据，以便每一类记录都有同等的代表性。这可以通过两种方式实现:欠采样和过采样。

**欠采样**是一种从数据集中移除多数类记录以使多数类记录和少数类记录的数量相等的技术。

**过采样**与欠采样正好相反，在这种技术中，使用 SMOTE 添加少数类记录，SMOTE 使用最近邻算法从可用数据中创建新样本。

## 参考

[1]张，s，张，c，杨，q . 2003 .数据挖掘的数据准备。*应用人工智能*，*17*(5–6)，第 375–381 页。

[2][https://www . analyticsvidhya . com/blog/2019/09/data-scientists-guide-8-types-of-sampling-techniques/](https://www.analyticsvidhya.com/blog/2019/09/data-scientists-guide-8-types-of-sampling-techniques/)

[3][https://towards data science . com/box plot-for-anomaly-detection-9 EAC 783382 FD](https://towardsdatascience.com/boxplot-for-anomaly-detection-9eac783382fd)

[4][https://www . r-bloggers . com/2020/06/why-balancing-your-dataset-is-important/](https://www.r-bloggers.com/2020/06/why-balancing-your-data-set-is-important/)

[5][https://www . analyticsvidhya . com/blog/2021/10/handling-missing-value/](https://www.analyticsvidhya.com/blog/2021/10/handling-missing-value/)

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)