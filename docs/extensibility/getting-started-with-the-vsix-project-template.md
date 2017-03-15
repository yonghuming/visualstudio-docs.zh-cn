---
title: "Getting Started with VSIX 项目模板 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK，VSIX 项目模板"
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Getting Started with VSIX 项目模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要创建一个扩展，或进行打包以进行部署现有扩展插件，可以使用 VSIX 项目模板。 VSIX 项目模板具有 Visual Basic 和 Visual C\# 版本，并作为 Visual Studio SDK 的一部分安装。  
  
 VSIX 项目模板只是由源 source.extension.vsixmanifest 文件，其中包含有关扩展的信息和发布时附带的资产。  
  
 若要查找 VSIX 项目模板，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 部署自定义项目模板使用 VSIX 项目模板  
 下列步骤显示如何使用 VSIX 项目进行打包，您可以与其他开发人员共享或上载到 Visual Studio 库项目模板。  
  
1.  创建项目模板。  
  
    1.  打开用来创建模板的项目。 此项目可以是对任何项目类型。  
  
    2.  在**“文件”**菜单上，单击**“导出模板”**。 完成该向导的步骤。  
  
         在 %USERPROFILE%\\My Documents\\Visual Studio 中创建一个.zip 文件 *\< 版本 \>*\\My Exported Templates\\。  
  
2.  创建一个空的 VSIX 项目。  
  
     在**文件**菜单上，单击**新建**，然后单击**项目**。 选择 **Visual Basic** 或 **Visual C\#**。 在选定节点下选择 **扩展性**, ，然后选择 **VSIX 项目**。  
  
3.  将.zip 文件添加到项目。 设置其 **复制到输出目录** 属性设置为 `Copy Always`。  
  
4.  在 **解决方案资源管理器**, ，双击 `source.extension.vsixmanifest` 文件以打开该文件 **VSIX 清单设计器**, ，然后进行以下更改 ︰  
  
    -   设置 **产品名称** 字段拖至 **我的项目模板**。  
  
    -   设置 **产品 ID** 字段拖至 **MyProjectTemplate\-1**。  
  
    -   设置 **作者** 字段拖至 **Fabrikam**。  
  
    -   设置 **说明** 字段拖至 **我的项目模板**。  
  
    -   在 **资产** 部分中，添加 **Microsoft.VisualStudio.ProjectTemplate** 键入并设置其路径为.zip 文件的名称。  
  
5.  保存并关闭源 source.extension.vsixmanifest 文件。  
  
6.  生成项目。  
  
7.  在输出目录中，双击.vsix 文件。  
  
8.  一个 **VSIX 安装程序** 出现消息框。 按照说明操作以安装扩展。  
  
9. 关闭 Visual Studio，然后重新打开它。  
  
10. 选择 **扩展和更新** \(上 **工具** 菜单\)，然后选择 **模板** 类别。 可用扩展插件之一应为 **我的项目模板**。  
  
11. 新的项目模板将出现在 **新项目** 中与原始项目模板相同的位置的对话框。 例如，如果您创建了一个名为模板 **VB 控制台** 从 Visual Basic 控制台应用程序， **VB 控制台** 为 Visual Basic 的同一个窗格中显示 **控制台应用程序** 模板。  
  
#### 若要在新项目对话框中指定的模板位置  
  
1.  模板文件夹位于 *Visual Studio 安装路径*\\Common7\\IDE\\ProjectTemplates 和 *Visual Studio 安装路径*\\Common7\\IDE\\ItemTemplates 目录。 在新建项目对话框的最高级别部分的名称与模板文件夹的名称不完全匹配。 如果它们不同，使用模板文件夹的名称。  
  
     将.vsix 文件扩展名更改为.zip，，然后打开该文件。  
  
2.  使用与模板应显示在新建项目对话框中的部分相同的名称创建一个新的文件夹。  
  
3.  如果该模板将出现在一个子节中，创建具有相同名称的子文件夹。  
  
4.  将模板的.zip 文件移到新文件夹。  
  
5.  将.zip 扩展名改为.vsix。  
  
6.  打开的 VSIX 清单。  
  
7.  在 VSIX 清单中，更新 **资产** 的模板，使其指向包含的模板文件的目录树的根路径。 例如，如果模板是在 \\CSharp\\Windows，该引用应指向 \\CSharp。