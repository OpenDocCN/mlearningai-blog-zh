# 使用 Parsehub 简化网页抓取

> 原文：<https://medium.com/mlearning-ai/web-scraping-made-easy-with-parsehub-a-web-scraping-application-b265d6b5a4a7?source=collection_archive---------1----------------------->

# 介绍

网络搜集一直是每个数据科学家为他们的项目获取高质量数据所必须经历的艰苦过程。网络抓取需要你使用编码知识、硬件和时间，这些用在其他地方会更好。Parsehub 是一个专门为帮助抓取网站而开发的应用程序，它执行大多数 web 抓取库会做的所有任务，不需要任何编码知识，并且完全免费。

# 安装 Parsehub

前往[https://www.parsehub.com](https://www.parsehub.com/register)注册一个账户。别担心，完全免费。你收集的数据将被直接发送到你的邮箱里。它还会在完成抓取后向您发送通知。

![](img/9f9c3e7db0af89f667f5d54f11f7d431.png)

Registering for a parsehub account

接下来，转到下载页面，在您当前拥有的操作系统上安装他们的应用程序。按照说明操作，直到您的设备上安装了 parsehub。

![](img/19da07db13f45fd80237033217b7d5a0.png)

Downloading the application on your desktop

# 抓取网站

打开应用程序后，您可能需要登录您的帐户。之后，您可以尝试可选教程。我将举例说明一个网站 Tripadvisor 网站被刮。

![](img/420090482f3493e99afb082a5a262767.png)

一旦你点击了新的项目，你将被要求输入你想要抓取的网站的网址。我输入了一个 trip advisor 位置的 URL 进行搜索。

![](img/6f71cc2b85bb232c7d1fd295bed6f84d.png)

您将被发送到默认的主模板。请注意，在开始时，整个页面被选中。您的第一个主要选择应该是您想要提取的实体。我想提取每个名字，你也可以选择实体的整个 div 块。

选择实体后，使用“相对选择”来选择相对于它的实体。为此，请转到选择实体旁边的添加选项，然后单击相对选择操作。接下来，单击选定的实体，然后单击您选择的相关实体。

![](img/95a483cfb491d53125073e2f8bf240a4.png)

Using Relative Select

您可以对一个主要选择使用多个相对选择操作。我继续将每个图像的 URL 和描述添加到“Name”选择动作中。接下来要做的事情是转到下一页。首先对主模板进行一个新的选择操作，然后选择 next page 按钮。然后给它添加一个点击动作。

![](img/29ec63e423580c8ae75998902a65feab.png)

你将被询问这是否是一个下一页按钮，以及你想要下一页被点击多少次。因为总共只有两页，所以我选择了选项 1。一旦你做到了这一点，确保下一个页面的行动是在提取后，而不是在此之前，否则，爬虫不会移动到下一个页面没有提取第一个。

![](img/953a1b8d2badc2ee5b9d1fd2c0459840.png)

在此之后，剩下唯一要做的事情就是提取页面，单击“获取数据”按钮提取页面，转到项目运行页面。点击运行后，页面将被提取。您还可以尝试运行一次测试，看看项目将如何实时执行。

![](img/54018f2bde8bc2d9acc4e3626c8c6f86.png)

项目执行后，需要一段时间运行，然后您可以在驱动器或应用程序上下载 csv、JSON、csv 格式的数据。网页将使用 parsehub 服务器提取，而不是在您的设备上，因此没有必要保持应用程序打开。一旦解压缩完成，您将收到一个通知[注意，在免费版本中，可以解压缩的页面数量是有限的]。

![](img/72b0b7c779e95ba388a872a1ebc9a452.png)

# 尾注

本教程只是 parsehub 所能做的一小部分，更多细节请查看应用程序的 parsehub 教程。