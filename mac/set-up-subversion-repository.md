---
title: "在 Visual Studio for Mac 中设置 Subversion 存储库"
description: "使用 Visual Studio for Mac 中的 Git 和 Subversion。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: ea2dffed0b9091dae61792783eb83c103ca9375c
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---

# <a name="setting-up-a-subversion-repository"></a>设置 Subversion 存储库

Subversion 是一个集中式版本控制系统。 这表示，有一个服务器包含所有文件和修订，用户可从中签出任何文件的任何版本。 从远程 Subversion 存储库中签出文件时，用户将收到该时间点的存储库快照。

在开始使用 Subversion 之前，必须安装 Xcode 命令行工具，因为它们包含正确的 SVN 包。 可使用以下命令检查终端中是否安装了 SVN：

`svn h`

1. 在线创建免费 SVN 存储库。 此示例中使用了 [Assembla](https://app.assembla.com/)。 创建后，将提供用于连接到此存储库的 URL： 

    ![获取并复制 SVN URL](media/version-control-subversion1-sml.png)

2. 打开或创建一个 Visual Studio for Mac 项目。

3. 右键单击该项目并选择“版本控制”>“在版本控制中发布...”： 

    ![开始发布项目](media/version-control-subversion2.png)

4. 在“连接到存储库”选项卡中，从顶部下拉菜单中选择“Subversion”。

5. 输入步骤 1 中获取的 URL。 默认情况下，这应填充其他字段： 

    ![选择“存储库”和“输入详细信息”对话框](media/version-control-subversion3.png)

7. 单击“确定”，然后按“发布”确认。

7. 可能提示你为创建存储库的网站输入凭据。 按照下图输入信息：

    ![](media/version-control-subversion5.png)

8.  现在，在版本控制菜单中，应可见所有可用的版本控制命令。


