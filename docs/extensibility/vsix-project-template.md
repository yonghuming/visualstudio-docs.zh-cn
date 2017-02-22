---
title: "VSIX 项目模板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "部署包"
  - "发布扩展"
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# VSIX 项目模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以使用 VSIX 项目模板将一个或多个 Visual Studio 扩展包装在一个 VSIX 项目，以及然后将包发布上 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847) Web 站点。  
  
 VSIX 部署支持 Vspackage、 程序集、 MEF 组件、 项目模板、 项模板，工具箱控件和自定义扩展插件类型。  
  
> [!NOTE]
>  若要使用 VSIX 项目，必须安装 Visual Studio SDK。 有关 Visual Studio SDK 的详细信息，请参阅 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 在哪里可以找到 VSIX 项目模板  
 VSIX 项目模板将在 **新项目** 对话框。 展开 **Visual Basic** 节点或 **Visual C\#** 节点，然后选择 **扩展性**。  
  
> [!TIP]
>  请确保该.NET Framework 4.5 或更高版本在顶部的下拉列表中指定 **新项目** 对话框。  
  
## VSIX 项目模板的用途  
 VSIX 项目模板具有以下两大主要用途:  
  
-   如果要部署项目模板、 项模板和已具有 VSIX 支持其他扩展。  
  
-   要包装为一个部署包的多个扩展的输出。  
  
 无需使用 VSIX 项目模板将 VSPackages 迁移或其他类型的已有 VSIX 支持的扩展部署。  
  
## 打包空 VSIX 项目中的扩展插件  
 您可以打包现有扩展插件或没有支持，方法是将它放置在空的 VSIX 项目中的 VSIX 扩展。 要包装的扩展必须支持的类型的 [VSIX 架构](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
#### 若要通过使用一个 VSIX 项目打包扩展  
  
1.  生成构成您的扩展插件的项目。  
  
2.  通过创建一个 VSIX 项目 **VSIX 项目** 模板。  
  
     在中打开 Source.extension.vsixmanifest **清单设计器**。  
  
3.  在 **资产** 选项卡上，选择 **新建** 按钮。  
  
     **添加新资产** 对话框随即出现。  
  
4.  在 **类型** 列表中，选择要添加的扩展的类型。  
  
5.  若要添加当前的解决方案 \(例如，项模板或已编译的程序集\) 中包括的扩展插件或内容元素，请执行以下步骤:  
  
    1.  在 **源** 列表中，选择 **当前解决方案中的项目**。  
  
    2.  在 **项目** 列表中，选择扩展插件的名称。  
  
    3.  在 **此文件夹中的嵌入** 框中，输入在其中以嵌入资产，然后选择的文件夹的名称 **确定** 按钮。  
  
6.  若要添加的扩展或不包含当前解决方案中的内容元素，请执行以下步骤:  
  
    1.  在 **源** 列表框中，选择 **文件系统上的文件**。  
  
    2.  在 **路径** 字段中，输入到扩展名为已编译或压缩文件的完整路径或使用 **浏览** 按钮以浏览到该文件。  
  
    3.  在 **此文件夹中的嵌入** 框中，输入在其中以嵌入资产，然后选择的文件夹的名称 **确定** 按钮。  
  
7.  如果想要包括的其他扩展您包，则将它们添加相同的方式。  
  
8.  生成解决方案。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 生成包含 VSIX 清单文件、 \[Content\_Types\].xml 文件中，以及所有添加到项目的扩展资产的.vsix 文件。  
  
## 请参阅  
 [VSIX 扩展架构 2.0 参考](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)