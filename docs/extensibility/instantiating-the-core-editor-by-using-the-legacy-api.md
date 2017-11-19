---
title: "使用旧版 API 实例化核心编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a82f420203b88bb94531401d061493621f3eba93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>使用旧版 API 实例化核心编辑器
编辑器负责文本编辑功能，如插入、 删除、 复制和粘贴。 它与由语言服务，如文本突出显示、 缩进和 IntelliSense 语句结束提供这些函数组合起来。  
  
 可以实例化三种方式之一中的核心编辑器的实例：  
  
-   显式创建实例的核心编辑器在窗口中。  
  
-   提供一个编辑器工厂，它返回核心编辑器的一个实例  
  
-   从项目层次结构中打开文件。  
  
 以下各节讨论如何使用旧的 API 来实例化编辑器。  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>显式打开核心编辑器实例  
 当显式获取核心编辑器的一个实例：  
  
-   获取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>以保存所编辑的文档数据对象。  
  
-   通过创建来创建文档数据对象的面向行表示<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>接口从<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>接口。  
  
-   设置<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>作为文档数据对象的实例的默认实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>接口，使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>方法。  
  
     主机<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>实例中<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>接口使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>方法。  
  
 此时，显示<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>接口提供了一个窗口，其中包含核心编辑器的一个实例。  
  
 但是，这不是非常有用实例，因为它不具有键盘快捷方式，或访问高级功能。 若要获取键盘快捷方式和高级的功能的访问权限：  
  
-   使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法语言服务和编辑器是使用文档数据对象进行关联。  
  
-   创建你自己的快捷键，或通过设置使用的系统默认<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>对象显示属性。 若要执行此操作，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>方法替换<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>属性。  
  
     获取和使用非标准的快捷键，以便生成它们使用.vsct 文件。 有关详细信息，请参阅 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>如何使用编辑器工厂获取核心编辑器  
 实现与编辑器工厂使用的核心编辑器时<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法，请按照上一节来显式承载中所述的所有步骤<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>文档数据对象，在<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>对象。  
  
 若要显示的文本，获得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>接口从<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>对象并调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。  
  
 若要向编辑器提供语言服务，调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法内的<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。  
  
 若要获取键盘快捷方式，与上一节中，不同的默认你使用命令行上下文返回<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法获取从核心编辑器时<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。  
  
 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法返回的相同命令 GUID 作为文本编辑器、 核心编辑器实例自动获取默认键盘快捷方式。  
  
 有关常规信息，请参阅[演练： 创建核心编辑器和注册编辑器文件类型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在核心编辑器](../extensibility/inside-the-core-editor.md)   
 [打开和保存项目项](../extensibility/internals/opening-and-saving-project-items.md)   
 [演练： 创建核心编辑器和注册编辑器文件类型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)