# 对抗性验证解释！！✨☀️

> 原文：<https://medium.com/mlearning-ai/adversarial-validation-explained-%EF%B8%8F-54b18bdbc9e?source=collection_archive---------2----------------------->

# 对抗验证

有一种有趣的技术可以估计训练数据和测试数据之间的差异程度。这被称为**“对抗验证”**

![](img/2315b4f122d8ca44912ccb69b5cdc68f.png)

**Canva template**

***所以我用一个例子给你解释一下这个*** *:*

*   假设我们有一个问题的训练数据和测试数据。我们会把训练和测试数据互相结合。
*   然后，如果我们用 1 对训练数据进行编码，用 0 对测试数据进行编码，我们将得到一个目标值为二进制的全新数据集。
*   这个问题变成了目标值为 0 & 1 的二元类分类问题。
*   因此，我们将使用任何机器学习模型来训练这个数据集，以进行分类和评估。我们将使用 ROC AUC 作为衡量标准。

> 对抗性验证依赖于 ROC-AUC 的计算，该图显示了在**不同分类阈值**下**真阳性率**和**假阳性率**。该曲线下的面积(AUC)衡量模型的性能。
> 
> 完美的模型会有 1.0 的面积，而只会犯错的模型会有 0.0 的面积。

***所以我们会得到两个场景:***

1)如果 **ROC-AUC 得分大于 0.9** ，这将告诉我们训练数据和测试数据的**分布**不同**。这是因为由于不同的分布，该模型能够将目标分为两个不同的组。**

**2)**ROC-AUC 得分接近 0.5** ，那么这将告诉我们训练数据和测试数据的**分布**是**相同的**。这是因为由于相同的分布，该模型不能将目标分成两个不同的组。**

**因此，该技术将帮助我们确定训练和测试数据中的**数据完整性**和**一致性**。**

****资料来源:**
在阅读 2022 年 5 月 7 日的 bnomial 问题时，发现这个问题非常有用。所以，我想和大家分享我的解释😃
—>[https://today.bnomial.com/](https://today.bnomial.com/)
—>[https://blog.zakjost.com/post/adversarial_validation/](https://blog.zakjost.com/post/adversarial_validation/)**

**感谢阅读！**

**关注我了解更多关于 DS 和 ML 的内容。**

**[https://medium . com/mlearning-ai/mlearning-ai-submission-suggestions-b 51e 2b 130 bfb](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)**