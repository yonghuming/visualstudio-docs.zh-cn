---
title: "VSIX 项目模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24a2937b37aa339f85e197f6ff2bb49cbb0ce86f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-project-template"></a>VSIX 项目模板
你可以使用 VSIX 项目模板将一个或多个 Visual Studio 扩展包装在一个 VSIX 项目中，然后将包发布上[Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)Web 站点。  
  
 VSIX 部署支持 Vspackage、 程序集、 MEF 组件、 项目模板、 项模板、 工具箱控件和自定义的扩展类型。  
  
> [!NOTE]
>  若要使用 VSIX 项目，必须安装 Visual Studio SDK。 有关 Visual Studio SDK 的详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="where-to-find-the-vsix-project-template"></a>在哪里可以找到 VSIX 项目模板  
 VSIX 项目模板将在**新项目**对话框。 展开**Visual Basic**节点或**Visual C#**节点，然后选择**扩展性**。  
  
> [!TIP]
>  请确保该.NET Framework 4.5 或更高版本在顶部的下拉列表中指定**新项目**对话框。  
  
## <a name="uses-of-the-vsix-project-template"></a>VSIX 项目模板的用途  
 VSIX 项目模板有两个主要用途：  
  
-   如果要部署项目模板、 项模板和已没有 VSIX 支持其他扩展。  
  
-   要包装为一个部署包的输出的多个扩展。  
  
 无需使用 VSIX 项目模板来部署 Vspackage 或其他种类的已有 VSIX 支持的扩展。  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>打包的空 VSIX 项目中的扩展  
 你可以打包现有扩展或尚不包含支持，方法是将它放置在一个空的 VSIX 项目中的 VSIX 扩展。 要包装的扩展必须支持的类型[VSIX 架构](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>若要将扩展打包使用 VSIX 项目  
  
1.  构成你的扩展将项目生成。  
  
2.  使用创建 VSIX 项目**VSIX 项目**模板。  
  
     在中打开 Source.extension.vsixmanifest**清单设计器**。  
  
3.  上**资产**选项卡上，选择**新建**按钮。  
  
     **添加新资产**对话框随即出现。  
  
4.  在**类型**列表中，选择要添加的扩展的类型。  
  
5.  若要添加将包含在当前解决方案 （例如，项模板或已编译的程序集） 的扩展或内容元素，请执行以下步骤：  
  
    1.  在**源**列表中，选择**当前解决方案中的项目**。  
  
    2.  在**项目**列表中，选择扩展的名称。  
  
    3.  在**此文件夹中的嵌入**框中，输入在其中以嵌入资产，然后选择的文件夹的名称**确定**按钮。  
  
6.  若要添加扩展或不包括当前解决方案中的内容元素，执行以下步骤：  
  
    1.  在**源**列表框中，选择**在文件系统上的文件**。  
  
    2.  在**路径**字段中，到编译或压缩扩展文件中，输入的完整路径或使用**浏览**按钮以浏览到该文件。  
  
    3.  在**此文件夹中的嵌入**框中，输入在其中以嵌入资产，然后选择的文件夹的名称**确定**按钮。  
  
7.  如果想要包括其他扩展。 你包，则将它们添加相同的方式。  
  
8.  生成解决方案。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成包含 VSIX 清单文件、 [Content_Types].xml 文件，和的所有扩展资产添加到项目的.vsix 文件。  
  
## <a name="see-also"></a>另请参阅  
 [VSIX 扩展架构 2.0 参考](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)