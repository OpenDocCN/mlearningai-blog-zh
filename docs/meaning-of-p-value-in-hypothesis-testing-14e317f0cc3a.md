# 假设检验中 P 值的意义。

> 原文：<https://medium.com/mlearning-ai/meaning-of-p-value-in-hypothesis-testing-14e317f0cc3a?source=collection_archive---------6----------------------->

每当我们进行假设检验时，我们都试图得出结论，而我们这样做的方式需要 p 值的概念。我们现实一点，学习一下统计学中 p 值的意义。

![](img/7470530e794b3e6dba0da98933e8ade4.png)

Photo by [Lars Bo Nielsen](https://unsplash.com/@lbnielsen?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

## 莱昂内尔·梅西 10 次尝试进 10 球:

梅西的表现太棒了。几天后，梅西的球迷 **H(o)** 和克里斯蒂亚诺·罗纳尔多的球迷 **H(a)** 之间爆发了一场争论。

H(a)说*“梅西只是运气好进了”*
H(o)说*“不可能，梅西是最棒的，他能证明”*

为了解决这个争论，梅西进行了一项测试来证明自己。

## **梅西的考验:**

***测试规则:*** *共 20 轮，每轮梅西有 10 次试举机会。如果梅西在 20 轮比赛中至少有一轮进满 10 球，那么他真的很有天赋，梅西的粉丝***将会获胜。
如果梅西在任何一轮中都没有进满 10 个球，那么他之前的 10 个球只是运气，克里斯蒂亚诺·罗纳尔多的球迷****【H(a)****获胜。**

## ***结果:***

*梅西 3/20 轮进满 10 球。⛳️*

*现在根据规则，梅西需要至少得分 1/20 才能获胜，他得分 3/20，这使他成为明显的赢家。
*恭喜梅西的粉丝****H(o)****😅 🎊**

## **你抓住上面故事中的 p 值了吗？问答环节。**

**测试说，如果梅西至少进球 1/20 次那么他就赢了，
因此， *1/20 = 0.05 = 5%*
而这 5%是谁决定的？进行测试的人。
*这也叫显著性水平(alpha)* 。**

*****5%以上会发生什么？***
梅西进球至少 1/20 的概率走高。H(o)赢了！**

*****低于 5%会怎样？***
梅西得分至少 1/20 的概率往下走。H(a)赢了。**

*****那么 p 值是多少呢？***
梅西进球的数值，也就是 **3/20** 。**

***p 值= 3/20 = 0.15 = 15%*
自 *p 值**(15%)>alpha(5%)*，H(o)胜！
***什么是 H(o)？梅西得分那么高完全是正常的。*****

*****如果梅西 0/20 进球会怎样？***
那么， *0/20 = 0%*
*p 值= 0.00%*
自 *p 值(0%) < alpha (5%)* ，H(a)胜！
***什么是 H(a)？梅西的 10 球记录纯粹是运气。侥幸投篮！*****

*****如何计算 p 值？***
p-value 是梅西在任何一个常规日观察到 10 个进球的*概率，也就是 H(o)所说的梅西因为技术娴熟随时可以做到。***

***P(10 个目标|任意常规日)= p 值= 3/20 = 0.15 = 15%***

**![](img/ffaa07ebaa4219ecc7afaea8fa5a255d.png)**

**Photo by [Rhett Lewis](https://unsplash.com/@historysoccerof?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)**

## ****牛逼的家伙们，现在来看看一本教科书是怎么描述 p 值的:****

**让我们形式化一些术语，
Event =你想要进行测试的一些事件。H(o) =零假设。
H(a) =交替假设。
alpha = 0.05 = 5%(您可以自由选择测试的任何百分比)
p 值=假设零假设为真，观察到该事件的概率。
或者，P 值= P(事件| H(o))**

**如果 p 值>α，那么我们接受 H(o)。这意味着这种情况经常发生。
如果 p 值≤α，那么我们无法接受 H(o)。说明这种事件很少见。**

**我们完成了！简单吗？评论一下，让我知道。😃**

# **结论:**

1.  ***对 p 值有一个直观的理解对假设检验很重要。***
2.  **请记住，p 值只是在正常情况下发现极端事件的概率。**
3.  ***显著性水平α是在测试开始前设定的，p 值是我们计算来决定测试最终结论的唯一东西。***
4.  ***而且很简单！有耐心，你会做得更好。***

# ****联系我:****

*****邮箱****:saurav@guptasaurav.com* ***领英****:*[*https://www.linkedin.com/in/sauravgupta20*](https://www.linkedin.com/in/sauravgupta20/)**

> **即使停止的时钟一天也有两次是正确的。**

**[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)**