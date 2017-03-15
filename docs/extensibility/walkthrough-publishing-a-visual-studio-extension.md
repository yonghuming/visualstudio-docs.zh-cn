---
title: "演练︰ 发布 Visual Studio 扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 574af4ff2b3858201c13121475de02a763572f6b
ms.openlocfilehash: fcfb0724b89d60553d6686a0705ab1e9459014ce
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>演练︰ 发布 Visual Studio 扩展
本演练演示如何将 Visual Studio 扩展发布到 Visual Studio 库。 在您的扩展添加到库时，开发人员可以使用**扩展和更新**从中浏览新建和更新的扩展。  
  
## <a name="prerequisites"></a>先决条件  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="create-a-visual-studio-extension"></a>创建一个 Visual Studio 扩展  
 在这种情况下，我们将使用默认 VSPackage 扩展插件，但相同的步骤也适用于每一种扩展。  
  
1.  在名为 C# 中创建的 VSPackage`TestPublishing`具有菜单命令。 有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="test-the-extension"></a>测试此扩展  
 分发扩展之前，请生成并测试它以确保 Visual Studio 的实验实例中安装正确。  
  
1.  在 Visual Studio 中，开始调试。 若要打开的 Visual Studio 的实验实例。  
  
2.  在实验实例中，转到**工具**菜单，然后单击**扩展管理器**。 TestPublishing 扩展应显示在中心窗格中，并且启用。  
  
3.  在**工具**菜单上，请确保您看到测试命令。  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>将扩展发布到 Visual Studio 库  
 现在可以将扩展发布到 Visual Studio 库。  
  
1.  请确保你已经构建了您的扩展的版本，并且它是最新。  
  
2.  在 Web 浏览器中，打开 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkId=194329) 网站。  
  
3.  在右上角中，单击**登录 IN**。  
  
4.  使用您的 Microsoft 帐户登录。 如果还没有 Microsoft 帐户，您可以在这里创建一个。  
  
5.  单击“上载” 。  
  
6.  在**步骤 1︰ 扩展类型**，选择**工具**，然后单击**下一步**。  
  
7.  在**步骤 2︰ 上载**，您可以选择直接将上载到 Visual Studio 库或只需添加您自己的网站的链接。 在这种情况下选择**我希望上载我的工具**。 **选择您的控件**出现框。 单击**浏览**，然后在该项目的 \bin\Release 文件夹中选择 TestPublish.vsix。 单击“下一步” 。  
  
8.  在**步骤 3︰ 基本信息**，将显示源 source.extension.vsixmanifest 文件中的字段。 选择相应的**类别**并添加**标记**以帮助用户找到您的扩展。 您可能想要添加的更详细的摘要和说明 （描述必须至少 280 个字符长）。 保留**扩展类型**作为**Microsoft 扩展**和**成本类别**作为**试用版**。  
  
9. 阅读底部的页上的发布内容协议，并检查**我同意**。  
  
10. 单击**创建发布内容**。 此时将显示您的扩展插件将对带有页面尚未发布一条消息的 Visual Studio 库页。  
  
11. 单击“发布” 。  
  
12. 搜索您的扩展 Visual Studio 库。 应显示 TestPublish 扩展名的列表。  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>从 Visual Studio 库安装扩展  
 现在，该扩展已发布，在 Visual Studio 中安装它，并对其进行测试。  
  
1.  在 Visual Studio 中，在**工具**菜单上，单击**扩展和更新**。  
  
2.  单击**联机**TestPublish 然后搜索。 应显示 TestPublish 扩展名的列表。  
  
3.  单击 **“下载”**。 下载该扩展后，单击“安装” 。  
  
4.  若要完成安装，重新启动 Visual Studio。  
  
## <a name="removing-the-extension"></a>删除扩展  
 从 Visual Studio 库并从您的计算机，可以删除该扩展。  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>若要从 Visual Studio 库中删除扩展  
  
1.  打开[Visual Studio 库](http://go.microsoft.com/fwlink/?LinkId=194329)网站。  
  
2.  在中心，单击**My 扩展**。 此时将显示 TestPublish 的列表。  
  
3.  单击**删除**。  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>若要从您的计算机中删除扩展  
  
1.  在 Visual Studio 的“工具”  菜单中，单击“扩展管理器” 。  
  
2.  选择 TestPublish，然后单击**卸载**。  
  
3.  若要完成卸载，请重新启动 Visual Studio。

