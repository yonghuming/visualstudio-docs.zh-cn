---
title: "演练： 将内容类型链接到的文件名称扩展 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bfe19b8733a6ee5ffe3d038778e664a4a1455dbe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>演练： 将内容类型链接到文件扩展名
你可以定义您自己的内容类型，并将文件扩展名为链接到它，通过使用编辑器 Managed Extensibility Framework (MEF) 扩展。 在某些情况下，文件扩展名已定义由语言服务;不过，将它用于 MEF 你仍必须将其链接到的内容类型。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-mef-project"></a>创建 MEF 项目  
  
1.  创建 C# VSIX 项目。 (在**新项目**对话框中，选择**Visual C# / 可扩展性**，然后**VSIX 项目**。)将解决方案命名`ContentTypeTest`。  
  
2.  在**source.extension.vsixmanifest**文件中，转到**资产**选项卡，并设置**类型**字段**Microsoft.VisualStudio.MefComponent**、**源**字段**当前解决方案中的项目**，和**项目**字段到项目的名称。  
  
## <a name="defining-the-content-type"></a>定义的内容类型  
  
1.  添加一个类文件并将其命名`FileAndContentTypes`。  
  
2.  添加对下列程序集的引用：  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  添加以下`using`指令。  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  声明一个静态类，包含的定义。  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  在此类中，导出<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>名为"隐藏"，并声明为"text"其基本定义。  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>将文件扩展名为链接到的内容类型  
  
-   若要将此内容类型映射到文件扩展名，将导出<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>具有扩展名".hid"和内容类型"隐藏"。  
  
    ```csharp  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>将内容类型添加到编辑器导出  
  
1.  创建的编辑器扩展。 例如，你可以使用中所述的边距标志符号扩展[演练： 创建边距标志符号](../extensibility/walkthrough-creating-a-margin-glyph.md)。  
  
2.  添加在此过程中定义的类。  
  
3.  导出扩展类时，添加<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>的"隐藏"到它的类型。  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [语言服务和编辑器扩展点](../extensibility/language-service-and-editor-extension-points.md)