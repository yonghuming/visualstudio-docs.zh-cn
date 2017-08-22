---
title: "设置 Visual Studio for Mac Tools for Unity"
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.topic: article
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: c2290b1165b8d2688b280684e1251b929d002594
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>设置 Visual Studio for Mac Tools for Unity

本部分介绍如何开始使用 Visual Studio for Mac Tools for Unity。

## <a name="install-visual-studio-for-mac"></a>安装 Visual Studio for Mac

下载和安装 Visual Studio for Mac。 Visual Studio for Mac 的所有版本都支持 Visual Studio for Mac Tools for Unity，包括免费的社区版本：

* 前往 [visualstudio.com](https://www.visualstudio.com/) 下载 Visual Studio for Mac。
* Visual Studio for Mac Tools for Unity 将在安装过程中自动安装。
* 请按照[安装指南](/visualstudio/mac/installation)中的步骤获取其他安装帮助。

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>确认启用 Visual Studio for Mac Tools for Unity 扩展

虽然应默认启动 Visual Studio for Mac Tools for Unity 扩展，但也可以检查安装版本号确认这一点：

1.  在 Visual Studio 菜单中，选择“扩展...”。

  ![选择扩展](media/setup-vsmac-tools-unity-image1.png)

2.  展开“游戏开发”部分，确认 Visual Studio for Mac Tools for Unity。

  ![查看 Unity 条目](media/setup-vsmac-tools-unity-image2.png)

## <a name="install-unity"></a>安装 Unity

Visual Studio for Mac Tools for Unity 工具需要 5.6.1 或更高 Unity 版本。 所有 Unity 计划都使用 Visual Studio for Mac Tools for Unity，包括免费的个人计划。 前往 [store.unity.com](https://store.unity.com/) 下载 Unity。

> [!NOTE]
> 若要验证你的 Unity 版本是否启用了 Visual Studio for Mac Tools for Unity，请从 Unity 菜单中选择“关于 Unity”，并在对话框左下角查看“Microsoft Visual Studio Tools for Unity 已启用”文本。
>
>   ![关于 Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>配置用于 Visual Studio for Mac 的 Unity

Visual Studio 必须设置为 Unity 中的外部脚本编辑器：

1.  从 Unity 菜单选择“首选项...”。

  ![选择首选项](media/setup-vsmac-tools-unity-image4.png)

2.  在“首选项”对话框中，选择“外部工具”选项卡。

3.  从“外部脚本编辑器”下拉列表中，选择“Visual Studio”（如果列出此项），否则选择“浏览...”。

  ![选择 Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4.  如果已选择“浏览...”，导航到“应用程序目录”，选择“Visual Studio”，然后单击“打开”。

  ![选择“打开”](media/setup-vsmac-tools-unity-image6.png)

5.  在“外部脚本编辑器”列表中选择 Visual Studio 之后，关闭首选项对话框完成配置流程。

