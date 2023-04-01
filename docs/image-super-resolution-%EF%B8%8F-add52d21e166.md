# 图像超分辨率？！🖼️

> 原文：<https://medium.com/mlearning-ai/image-super-resolution-%EF%B8%8F-add52d21e166?source=collection_archive---------2----------------------->

你们中的一些人可能经历过你点击的图像被像素化了，你希望那个图像是高分辨率的而不是像素化的。

![](img/3e1b6cd4c571aae57c1c5deef0ebc975.png)

Photo by [Roméo A.](https://unsplash.com/@gronemo?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

这是深度学习算法的完美例子。有时由于一些技术故障，我们有模糊的照片或非常低比例的图像。深度学习通过创建相同的模型来解决这个问题。它将输入作为缩小的图像，并尝试通过深度学习方法放大像素来转换像素。

## 它在哪里有用？

图像超分辨率可以在许多任务中有所帮助，包括我们日常生活中的使用，从捕捉一些鸟类的图像到一些研究用途。实际上，无论图像是什么，我们都可以使用这种技术对图像进行上采样。

## 怎么才能做到呢？

图像恢复是一个由来已久的低级视觉问题，旨在从低质量图像恢复高质量图像。借助卷积网络或变压器，我们可以做到这一点。我们将能够提取图像像素形状和颜色之间的模式，并在此基础上增强它们。

在这项任务中，我们主要关注如何提取边缘和重要特征，以及如何增强它们以高分辨率创建它们。

## 一些研究论文也是这样做的吗？

有许多研究人员试图使用不同的技术来实现相同的目标，目前根据我的研究 **SwinIR:使用 Swin Transformer** 研究论文的图像恢复是最有前途的，他们已经实现了最高的**峰值信噪比** (PSNR)，即 32.22。在本文中，他们使用变压器结构来实现它

## 变压器组

转换器的目标是在不丢失我们提供的信息的情况下提取特征(在这种情况下，信息是指我们将提供给模型的像素值。)

## 研究论文的链接，如果你想深入研究这个主题的话😃

*   论文与代码主页为图像超分辨率【https://paperswithcode.com/task/image-super-resolution 
*   基于 SWIN 变形金刚的图像恢复研究论文[https://papers with code . com/paper/swinir-image-restoration-using-SWIN](https://paperswithcode.com/paper/swinir-image-restoration-using-swin)

> 感谢你阅读我的博客:)关注更多，在评论中向我问好，这给了我写更多博客的鼓励:)祝你有美好的一天:)

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)