---
title: "Getting Started with VSIX 项目模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 33f29ebabbb40e747b2b321fcb1b3b5598284a28
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-the-vsix-project-template"></a>Getting Started with VSIX 项目模板
若要创建扩展或包部署的现有扩展，你可以使用 VSIX 项目模板。 VSIX 项目模板具有 Visual Basic 和 Visual C# 版本，并且作为 Visual Studio SDK 的一部分安装。  
  
 VSIX 项目模板只包含 source.extension.vsixmanifest 文件中，其中包含有关扩展的信息和发布时附带的资产。  
  
 若要查找 VSIX 项目模板，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>部署自定义项目模板使用 VSIX 项目模板  
 以下步骤演示如何使用 VSIX 项目打包可以与其他开发人员共享，也可以将上载到 Visual Studio 库的项目模板。  
  
1.  创建项目模板。  
  
    1.  打开从其创建模板的项目。 此项目可以是任何项目类型。  
  
    2.  在“项目”菜单上，单击“导出模板”。 完成向导的步骤。  
  
         %USERPROFILE%\My Documents\Visual Studio 中创建一个.zip 文件*\<版本 >*\My 导出模板\\。  
  
2.  创建一个空的 VSIX 项目。  
  
     在 **文件** 菜单上，单击 **新建** ，然后单击 **项目**。 选择**Visual Basic**或**Visual C#**。 在选定节点下选择**扩展性**，然后选择**VSIX 项目**。  
  
3.  向项目添加该.zip 文件。 设置其**复制到输出目录**属性`Copy Always`。  
  
4.  在**解决方案资源管理器**，双击`source.extension.vsixmanifest`文件中将其打开**VSIX 清单设计器**，然后进行以下更改：  
  
    -   设置**产品名称**字段**我的项目模板**。  
  
    -   设置**产品 ID**字段**MyProjectTemplate-1**。  
  
    -   设置**作者**字段**Fabrikam**。  
  
    -   设置**说明**字段**我的项目模板**。  
  
    -   在**资产**部分中，添加**Microsoft.VisualStudio.ProjectTemplate**键入，并将其路径设置为.zip 文件的名称。  
  
5.  保存并关闭 source.extension.vsixmanifest 文件。  
  
6.  生成项目。  
  
7.  在输出目录中，双击.vsix 文件。  
  
8.  A **VSIX Installer**出现消息框。 按照说明安装扩展。  
  
9. 关闭 Visual Studio，然后重新打开它。  
  
10. 选择**扩展和更新**(上**工具**菜单)，然后选择**模板**类别。 可用扩展之一应是**我的项目模板**。  
  
11. 新的项目模板显示在**新项目**与原始的项目模板位于同一位置中的对话框。 例如，如果你创建一个名为模板**VB 控制台**从 Visual Basic 控制台应用程序， **VB 控制台**为 Visual Basic 的同一窗格中显示**控制台应用程序**模板。  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>若要在新项目对话框中指定的模板位置  
  
1.  模板文件夹位于*Visual Studio 安装路径*\Common7\IDE\ProjectTemplates 和*Visual Studio 安装路径*\Common7\IDE\ItemTemplates 目录。 新项目对话框中的顶级部分的名称与模板文件夹的名称不完全匹配。 如果它们不同，使用模板文件夹的名称。  
  
     将.vsix 文件扩展名更改为.zip，，然后打开该文件。  
  
2.  使用与该模板应出现在新项目对话框的部分相同的名称创建一个新文件夹。  
  
3.  如果要在子部分中显示模板，创建具有相同名称的一个子文件夹。  
  
4.  将.zip 模板文件移到新文件夹。  
  
5.  将.zip 扩展名更改为.vsix。  
  
6.  打开的 VSIX 清单。  
  
7.  在 VSIX 清单中，更新**资产**模板使它指向包含模板文件目录树的根的路径。 例如，如果该模板正在 \CSharp\Windows，引用应指向 \CSharp。