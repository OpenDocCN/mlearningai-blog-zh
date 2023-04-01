# 不用保持机器运转就能训练 ML 模型！

> 原文：<https://medium.com/mlearning-ai/training-ml-models-without-keeping-your-machine-running-abe7a844a45a?source=collection_archive---------6----------------------->

![](img/9557d9089bafdf3dcf1302b14ad40fab.png)

Photo by [Lukas Blazek](https://unsplash.com/@goumbik?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

如果你正在学习机器学习，你可能已经观察到训练模型是一个乏味的过程，如果你有更大的架构模型，可能需要很长时间来运行和保存模型。

对于训练模型，如果你正在使用 Google Colab，那么你一定经历过运行时在一段时间不活动(可能不到 1/2 小时)后断开连接

另一种选择是 Kaggle，但使用 Kaggle，你无法在谷歌驱动器中存储数据，但尽管你可以在 Kaggle 数据集中存储任何你想要的数据集，你可以从那里使用它。

关于 Kaggle 最好的部分是，在设置您的笔记本运行并存储您想要存储的结果后，您甚至可以在没有互联网连接的情况下继续运行笔记本(在这种情况下，我们希望将我们的模型与`model.save`和一些输出存储在 CSV 中)

存储数据并完成笔记本后，您可以使用笔记本输出文件(在运行和保存时由 Kaggle 保存)访问您保存的模型和一些其他输出。让我们看看这样做有什么要求。

## 要求:

*   你应该有你的卡格尔帐户
*   您应该在 Kaggle 上存储一个想要处理的数据集。
*   是的，还有一些关于 PyTorch 的知识🔥或者 TensorFlow 来运行和保存我们的模型

## 步骤:

1.  在 Kaggle 中创建新的代码笔记本。
2.  使用右上角导航部分的添加数据按钮添加数据
3.  在笔记本右侧面板的帮助下将运行时间更改为 GPU(GPU 训练您的模型更快),它在加速器部分
4.  通过在代码单元中运行`!nvidia-smi`,确保您正在 GPU 上运行
5.  创建模型构建和保存文件
6.  确保您的代码中没有错误。(如果您的代码在顺序执行中包含错误，则保存过程可能会失败)
7.  确保你的模型不超过 9 小时
8.  创建并拥有你想要的所有代码，你必须使用`model.save`函数存储模型，并再次进行最后一次检查，确保一切正常。
9.  单击屏幕右上角的保存版本后，确保您单击的是保存并提交更改，而不是快速保存(快速保存不会保存您的输出，而保存并提交会保存您的输出)
10.  单击保存并提交后，您将在笔记本电脑的右下角通知部分看到一条消息，说明您的文件正在执行，您可以关闭浏览器，甚至可以在执行过程中关闭计算机。
11.  运行完你的笔记本后，Kaggle 会通知你它已经运行完了

## 为什么需要这样做:

在 Kaggle 上的比赛中，当我们必须为现实世界的问题建立模型时，我们要处理大量 GB 的数据，这个模型建立过程肯定需要时间。

虽然 google collab 为您提供了类似 GPU 的特斯拉 T4，但它不会为您提供很长时间的 GPU，而 Kaggle 为您提供了特斯拉 P100 GPU，它没有特斯拉 T4 那么快，但对于完成我们的工作来说也一样快，它为我们提供了很长时间的 GPU(9 小时)。

在比赛中，你必须通过保存模型和建立模型来创建一个模型训练笔记本和模型推理笔记本，这个步骤非常有效

## 笔记本链接:

[](https://www.kaggle.com/somesh88/70-epochs-prediction-fast-ai) [## 70 个时代预测快速人工智能

### 使用 Kaggle 笔记本探索和运行机器学习代码|使用来自多个数据源的数据

www.kaggle.comY](https://www.kaggle.com/somesh88/70-epochs-prediction-fast-ai) 

您可以参考上面的笔记本，了解模型构建和培训步骤。笔记本电脑运行时间约为 7 小时。

> *感谢阅读我的博客:)关注更多，在评论中向我问好，这鼓励我写更多的博客:)祝你有美好的一天:)*

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)