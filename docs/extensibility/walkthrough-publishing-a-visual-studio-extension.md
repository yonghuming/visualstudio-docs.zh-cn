---
title: "演练： 发布 Visual Studio 扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8eac89a2bdde3b0a20ea3a98775de84a503f86c
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>演练： 发布 Visual Studio 扩展

本演练演示了如何将 Visual Studio 扩展发布到 Visual Studio 应用商店。 在你的扩展添加到应用商店时，开发人员可以使用**扩展和更新**从中浏览新扩展和更新扩展。

## <a name="prerequisites"></a>先决条件

 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-visual-studio-extension"></a>创建一个 Visual Studio 扩展

在这种情况下，我们将使用的默认 VSPackage 扩展，但相同的步骤也适用于每个类型的扩展插件。

1. 在 C# 中名为"TestPublish"具有菜单命令创建 VSPackage。 有关详细信息，请参阅[创建第一个扩展： Hello World](../extensibility/extensibility-hello-world.md)。

## <a name="package-your-extension"></a>将扩展打包

1. 更新了有关产品名称、 author 和版本的正确信息的扩展 vsixmanifest。

  ![更新扩展 vsixmanifest](media/update-extension-vsixmanifest.png)

2. 生成你的扩展**版本**模式。 现在你的扩展将打包为 VSIX \bin\Release 文件夹中。

3. 你也可以双击 VSIX 验证安装。

## <a name="test-the-extension"></a>测试此扩展

 分发扩展之前，生成，然后测试它以确保它 Visual Studio 的实验实例中正确安装。

1. 在 Visual Studio 中，开始调试。 若要打开 Visual Studio 的实验实例。

2. 在实验实例中，转到**工具**菜单，然后单击**扩展和更新...**.TestPublish 扩展应显示在中心窗格中，启用。

3. 上**工具**菜单上，请确保你看到测试命令。

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>将扩展发布到 Visual Studio 应用商店

1. 请确保你已经构建了你的扩展的版本，并且它是最新。

2. 在 web 浏览器中，打开[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)网站。

3. 在右上角中，单击**登录**。

4. 使用您的 Microsoft 帐户登录。 如果你没有 Microsoft 帐户，则可以在此时创建一个。

5. 单击**发布扩展**。  你将会导航到你的所有扩展的管理页。  如果你没有发布服务器帐户，系统将提示创建一个在此时间。

  ![将上载到应用商店](media/upload-to-marketplace.png)

6. 选择你想要用于上载你的扩展的发布服务器。  您可以通过单击左上角的发布服务器名称更改发布服务器。

  ![更改 Marketplace 发布者](media/change-marketplace-publisher.png)

7. 在**1： 上载扩展**，你可以选择将 VSIX 文件上载到 Visual Studio 应用商店的直接或只需添加您自己的网站的链接。 在这种情况下，我们将以上载我们的扩展，TestPublish.vsix。  拖放你的扩展或使用**单击**链接以浏览到该文件。  在项目的 \bin\Release 文件夹中找不到你的扩展。  单击 **“继续”**。

8. 在**2： 提供扩展的详细信息**，某些字段会自动填充从 source.extension.vsixmanifest 文件从你的扩展。  可在下面找到有关每项的更多详细信息：

    * **内部名称**将扩展的详细信息页的 URL 中使用。 例如，发布在发布服务器名称"myname"扩展和指定的内部名称为"myextension"将产生的 URL"marketplace.visualstudio\.com/items?itemName=myname.myextension"你的扩展详细信息页。
    
    * **显示名称**你的扩展。  这从 source.extension.vsixmanifest 文件中是自动填充。
   
    * **版本**数要上载的扩展。  这从 source.extension.vsixmanifest 文件中是自动填充。
    
    * **VSIX ID**是 Visual Studio 将使用你的扩展的唯一标识符。  如果你想要让您进行自动更新的扩展，这是必需的。  这从 source.extension.vsixmanifest 文件中是自动填充。
    
    * **徽标**了将用于你的扩展。  这将从如果提供的 source.extension.vsixmanifest 文件中是自动填充。
    
    * **简短说明**的你的扩展的用途。  这将从 source.extension.vsixmanifest 文件中是自动填充。
    
    * **概述**是包括屏幕快照以及有关你的扩展的作用的详细的信息的良好开端。
    
    * **支持的 Visual Studio 版本**允许您选择的 Visual Studio 的版本中将处理你的扩展。  你的扩展将仅安装到这些版本中。
    
    * **支持的 Visual Studio 版本**允许您选择哪个版本的 Visual Studio 中将处理你的扩展。  你的扩展将仅安装到这些版本。
    
    * **类型**。  扩展的最常见类型**工具**。
    
    * **类别**。  选取最多三个都适合你的扩展。
    
    * **标记**是关键字可帮助用户查找你的扩展。 标记可帮助提高你的扩展应用商店中搜索相关性。
    
    * **定价类别**是你的扩展的成本。
    
    * **源代码存储库**，可与社区共享你的源代码的链接。
    
    * **扩展允许问答**将允许用户在你的扩展入口页上保留问题。

9. 单击**保存并上载**。 你将转回你的发布者管理页。  尚未发布你的扩展。  若要将扩展悬停发布你的扩展项，然后单击**...**然后**公开**。  你可以查看如何扩展将如下所示在 Marketplace 上通过选择**查看详细信息**。  获取数字，请单击**报表**。  若要对你的扩展进行更改，请单击 **编辑*。

  ![扩展条目菜单](media/extension-entry-menu.png)

10. 单击后**设为公开**，你的扩展现在是公共。  搜索你的扩展 Visual Studio Marketplace。

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>从 Visual Studio 应用商店中安装扩展

发布该扩展后，在 Visual Studio 中安装它并对其进行测试。

1. 在 Visual Studio 中，在**工具**菜单上，单击**扩展和更新...**.

2. 单击**联机**TestPublish 然后搜索。

3. 单击 **“下载”**。 然后将安装安排扩展。

4. 若要完成安装，请关闭 Visual Studio 的所有实例。

## <a name="removing-the-extension"></a>删除扩展

从 Visual Studio 应用商店和你的计算机，可以删除该扩展。

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>若要从 Visual Studio Marketplace 中删除扩展

1. 打开[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)网站。

2. 在右上角中，单击**发布**扩展。  选取用于发布 TestPublish 发布服务器。  将显示 TestPublish 的列表。

3. 将鼠标悬停在的扩展条目并单击**...**和**删除...**你将需要确认你是否要删除该扩展。  单击“确定”。

### <a name="to-remove-the-extension-from-your-computer"></a>若要从你的计算机中删除扩展

1. 在 Visual Studio 中，在**工具**菜单上，单击**扩展和更新...**.

2. 选择 TestPublish，然后单击**卸载**。 然后将卸载安排扩展。

3. 若要完成卸载，请关闭 Visual Studio 的所有实例。
