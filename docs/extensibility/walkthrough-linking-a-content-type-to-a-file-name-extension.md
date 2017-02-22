---
title: "演练: 将内容类型链接到的文件扩展名 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，新的链接内容类型为文件扩展名"
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# 演练: 将内容类型链接到的文件扩展名
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以定义您自己的内容类型和链接到它的文件扩展名，通过使用编辑器 Managed Extensibility Framework \(MEF\) 扩展。 在某些情况下，文件扩展名已定义的语言服务;不过，以便将其与 MEF 您仍必须将其链接到内容类型。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建 MEF 项目  
  
1.  创建 C\# VSIX 项目。 \(在 **新项目** 对话框中，选择 **Visual C\# \/ 可扩展性**, ，然后 **VSIX 项目**。\) 将解决方案命名 `ContentTypeTest`。  
  
2.  在 **source.extension.vsixmanifest** 文件中，转到 **资产** 选项卡，并设置 **类型** 字段拖至 **Microsoft.VisualStudio.MefComponent**, 、 **源** 字段拖至 **当前解决方案中的项目**, ，和 **项目** 字段拖至项目的名称。  
  
## 将内容类型定义  
  
1.  添加一个类文件并将其命名 `FileAndContentTypes`。  
  
2.  添加对下列程序集的引用：  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  将以下代码添加 `using` 指令。  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  声明一个静态类，包含的定义。  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  在此类中，将导出 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 名为"隐藏"，并声明其基础定义是"text"。  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## 将文件扩展名为链接到内容类型  
  
-   若要将此内容类型映射到的文件扩展名，将导出 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 具有扩展名的".hid"和"隐藏的内容类型"。  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## 将内容类型添加到编辑器导出  
  
1.  创建一个编辑器扩展。 例如，可以使用中所述的边距标志符号扩展 [演练︰ 创建边缘字形](../extensibility/walkthrough-creating-a-margin-glyph.md)。  
  
2.  添加在此过程中定义的类。  
  
3.  在导出的扩展类时，将添加 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 的"隐藏"给它的类型。  
  
    ```c#  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## 请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)