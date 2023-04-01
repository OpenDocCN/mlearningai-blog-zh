# 设置用于浏览器访问的远程 Jupyter 实验室/笔记本服务器

> 原文：<https://medium.com/mlearning-ai/set-up-remote-jupyter-lab-notebook-server-for-remote-browser-access-2cef464f203e?source=collection_archive---------0----------------------->

![](img/9bd6b1814a809a77d60624e671df8ea2.png)

Photo by [Erik Witsoe](https://unsplash.com/@ewitsoe?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

作为一名机器学习发烧友，您很可能会在日常生活中使用 Jupyter Lab 或 Jupyter 笔记本电脑来处理您的数据并培训您的模型。然而，通常我们日常使用的计算机不够强大，无法处理大量的计算负载，如深度神经网络、庞大的数据集等。因此，在远程机器上运行代码是必不可少的，第一步是建立 Jupyter 实验室或笔记本电脑。

已经有许多在线方法来远程设置您的 Jupyter Lab 或笔记本电脑，但其中许多方法需要使用复杂的工具，这些工具很可能不会在不同平台上通用，或者会导致其他未知问题。今天，我们将向您展示一种不太流行的方法，即仅使用内置配置在 20 分钟内设置您的远程 Jupyter Lab。

# 目录

[🔥](#563b)
安装[🔥创建配置文件](#a528)
[🔥配置](#d9b8)
[🔥启动 jupyter lab/笔记本](#2606)
∘ [感谢收看！:)](#a9a6)
[附录](#16d4)

# 🔥装置

首先，您需要通过 SSH 连接您的服务器。本文不会对此进行扩展。

连接后，**更新**系统，确认 python 和 pip 安装正确。我使用的是 Ubuntu 20.04，我的 python 版本是 **3.8.10** 。要更新 Ubuntu，您可以

```
sudo apt update
sudo apt upgrade
sudo apt-get update
sudo apt-get upgrade
```

现在，您已经准备好安装 Jupyter 实验室或笔记本电脑了。由于 Jupyter Lab 日益流行，本文将以 Jupyter Lab 为例。要安装笔记本，在本文的所有命令中，您通常只需要用笔记本替换 lab。要使用 pip3 安装与您的系统兼容的最新 Jupyter Lab 版本，请执行以下操作

```
pip3 install jupyterlab
```

如果你没有点 3，那就做吧

```
sudo apt install python3-pip
```

你们都为下一步做好了准备！

# 🔥创建配置文件

您首先需要生成配置文件。我们将来会在配置文件中写入我们的配置。(同样，对于 Jupyter 笔记本，请在下面用笔记本替换实验室)

```
jupyter lab --generate-config
```

如果您想设置密码通过浏览器访问您的实验室，请执行以下步骤(可选，但建议)

```
jupyter lab password
```

通常-generate-config 命令会生成一个 **jupyter_lab_config.py** 文件到你的主目录的**。jupyter** 文件夹。然而，我们将在同一个目录下使用 json 文件，这更容易处理。要访问/创建它，您可以使用 nano(如果您的系统有它的话)这个命令兼容于 Jupyter Lab 和 Jupyter 笔记本

```
nano /home/ubuntu/.jupyter/jupyter_server_config.json
```

如果您已经设置了密码，您将看到一个 json 格式的文件，其中包含您的散列密码。

# 🔥安装ˌ使成形

在您的 json 文件中填写以下内容。记住，如果你有一个密码放在你的密码。(*配置兼容 jupyter lab 和 jupyter notebook*

```
{  
  "NotebookApp": {
    "password": "YOUR ENCRYPTED PASSWORD IS HERE",
    "allow_remote_access":true,
    "ip":"*",
    "port":80,
    "allow_root":true
  }
}
```

这里， **allow_remote_access** 和 **ip** 参数会给你远程访问的权限。设置 ip=*是至关重要的，这意味着实验室将监听所有 ip 地址并欢迎它们的连接。参数 **allow_root** 将允许您以 root 权限运行您的笔记本，因此您可以监听端口 80。

之后，按 **control+x，y，**和 **Enter** 退出并保存文件。现在，jupyter 端已经配置好了。

几个快速注释:

*   对于端口，80 只能在 root 权限下访问。默认端口是 8888，您也可以在这种情况下使用。
*   如果您正在使用云服务，请记住还要配置安全组以允许来自您的 IP 地址的所有入站和出站连接，这样您就可以远程访问服务器。如果您不知道如何做到这一点，您也可以使用 **ufw** 命令来配置安全策略。

# 🔥启动 Jupyter 实验室/笔记本

现在你一切都准备好了。要使用 Jupyter Lab / Notebook，只需在命令行中输入即可。

```
jupyter lab
```

但是，由于在您关闭 SSH 会话后，jupyter lab 进程也会自动暂停，您可以在 jupyter lab 命令前添加此命令，使 jupyter lab 在后台运行，因此在关闭终端会话后，您不必担心进程也会终止。

```
nohup jupyter lab > output.txt
```

我们通常会做什么:

```
sudo -E env "PATH=$PATH" jupyter lab --allow-root --collaborative
```

*   sudo 已启用，因此 jupyter 可以监听端口 80
*   **-E env "PATH=$PATH"** 用于防止环境被 sudo 命令搞乱
*   **—如果您想使用 sudo，allow-root** 命令是必不可少的
*   **—协作**命令支持与其他人的实时协作。

至此，快速教程完成！你可以打开你的浏览器，输入服务器的 ip 地址(如果你需要的话，带端口)，它应该会自动打开。

## **感谢观看！:)**

# 附录

这里有一些快速笔记

要查看 jupyter 服务器的进程 ID，因为您之前使用了 **nohup** ，请键入

```
ps -ax|grep jupyter
```

要停止它，只需使用**杀死**命令

```
kill [jupyter ID]
```

启用扩展功能(在最新版本中无需手动操作)

```
sudo pip3 install -e jupyter_contrib_nbextensions
jupyter contrib nbextension install --user
```

[](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb) [## Mlearning.ai 提交建议

### 如何成为 Mlearning.ai 上的作家

medium.com](/mlearning-ai/mlearning-ai-submission-suggestions-b51e2b130bfb)