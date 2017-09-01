---
title: "在 Visual Studio for Mac 中设置 Git 存储库"
description: "使用 Visual Studio for Mac 中的 Git 和 Subversion。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 9f25eda17648ba7eb3c264660ee0eb3b8eee166c
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---

# <a name="setting-up-a-git-repository"></a>设置 Git 存储库

Git 是分布式版本控制系统，使团队可以同时在同一文档上工作。 这意味着有一个单一服务器包含所有文件，但从此中央源中签出存储库时，整个存储库都会被克隆到本地计算机。

虽然许多远程主机支持许使用 Git 进行版本控制，但最常用的是 GitHub。 虽然下面的示例使用 GitHub 主机，但可使用任何 Git 主机在 Visual Studio for Mac 中进行版本控制。

若要使用 GitHub，请确保先创建并配置一个帐户，再执行以下步骤。 

## <a name="creating-a-remote-repo-on-github"></a>在 GitHub 上创建远程存储库

虽然下面的示例使用 GitHub 主机，但可使用任何 Git 主机在 Visual Studio for Mac 中进行版本控制。

要设置 Git 存储库，请执行以下步骤：

1. 在 github.com 上创建新 Git 存储库：

    ![创建新 Git 存储库](media/version-control-git1-sml.png)

2. 设置存储库名称、说明和隐私。 请勿初始化存储库。 将 .gitignore 和许可证设置为“无”：

    ![设置 Git 存储库的详细信息](media/version-control-git2.png)

3. 下一个位置提供一个选项，用于显示 HTTPS 或 SSH 地址，并将其复制到刚创建的存储库：

    ![查看和复制地址](media/version-control-git3.png) 要将 Visual Studio for Mac 指向此存储库，需要 HTTPS 地址。


## <a name="publishing-an-existing-project"></a>发布现有项目

4. 返回到 Visual Studio for Mac 中打开的项目。 

5. 在菜单栏中，选择“版本控制”>“在版本控制中发布...”：

    ![开始在 Visual Studio for Mac 中签出](media/version-control-git4-sml.png)

6. 这将显示“选择存储库”对话框。 选择“已注册存储库”选项卡，然后按“添加”按钮：

    ![](media/version-control-git5.png)

7. 输入要在本地显示的存储库名称，然后粘贴步骤 #3 中的 URL。 “存储库配置”对话框应如下所示。 按“确定”： 

    ![输入 Git 详细信息对话框](media/version-control-git6.png)

    请注意，也可使用 SSH 连接到 Git。

8. 要尝试将应用发布到 Git，请选择刚创建的存储库，并确保“模块名称”和“信息”文本字段都已完成：

    ![尝试将应用发布到 Git](media/version-control-git7.png)

9. 单击“好的”，然后从警报对话框中单击“发布”。

10. 如果尚未在 Visual Studio for Mac 首选项中输入 Git 凭据，请于现在输入。 首先需要创建访问令牌，该令牌可用于替代密码。 请按照 Git [访问令牌](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)文档中的步骤执行此操作。

11. 输入用户名和个人访问令牌，然后按“好的”：

    ![输入 Git 用户名和密码](media/version-control-git9-sml.png)

12. 几秒钟后，会发布初次提交的解决方案。 可通过浏览“版本控制”菜单项进行确认，该菜单中应已填充了许多选项： 

    ![“版本控制”菜单](media/version-control-git10.png)

13. 开始进行其他更改时，请选择“发布更改...”将更改推送到“远程”存储库。 这可让所有相应的用户在 github.com 上进行查看： 

    ![将更改推送到远程存储库](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>发布新项目

“新建项目”对话框可用于通过 Git 发布新项目。 要启用该功能，请选择“使用 Git 进行版本控制。” 复选框，如以下屏幕截图所示。 这将初始化存储库，并添加一个可选 .gitignore 文件：

![将更改推送到远程存储库](media/version-control-git12.png)

## <a name="troubleshooting"></a>疑难解答

如果在使用空远程存储库初始化项目时遇到问题，可尝试执行以下步骤：

- 转到解决方案文件夹。
- 按 `Command + Shift + . ` 显示隐藏的文件和文件夹。
- 若有 `.git` 文件夹，请删除它。
- 若有 `gitignore` 文件，请删除它。
- 按 `Command + Shift + . ` 隐藏文件和文件夹。
- 在 VS for Mac 中打开解决方案。
- 在 Solution Pad 上选择解决方案节点。
- 浏览到“版本控制”菜单，并选择“在版本控制中发布”。
- 执行上述教程中的步骤 6 及之后的步骤。
