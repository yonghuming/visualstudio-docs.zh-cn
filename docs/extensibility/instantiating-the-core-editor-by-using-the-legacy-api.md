---
title: "实例化使用旧 API 的核心编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 29
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e18118d73d46aeee7612eb7dff64f778726778f0
ms.lasthandoff: 02/22/2017

---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>实例化使用旧 API 的核心编辑器
编辑器中负责进行文本编辑功能，如插入、 删除、 复制和粘贴。 它将结合这些函数所提供的语言服务，如文本着色、 缩进和 IntelliSense 语句结束。  
  
 您可以实例化中有三种方法的核心编辑器的实例︰  
  
-   显式创建实例核心的编辑器窗口中。  
  
-   提供编辑器工厂，它返回一个核心编辑器的实例  
  
-   从项目层次结构中打开一个文件。  
  
 以下各节讨论如何使用传统的 API 来实例化编辑器中。  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>显式打开的核心编辑器实例  
 当显式获取核心编辑器的实例︰  
  
-   获取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>以保存所编辑的文档数据对象。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
-   通过创建来创建行面向对象的表示形式文档数据<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>接口从<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>接口。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
-   设置<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>作为文档数据对象的实例的默认实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>接口，使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>方法。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
     主机<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>接口使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>  
  
 在这种情况下，显示<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>接口提供了一个窗口，其中包含的核心编辑器实例。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>  
  
 但是，这不是非常有用的实例，因为它不具有快捷方式键，或访问的高级功能。 若要获取对键盘快捷方式和高级的功能的访问︰  
  
-   使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法，以将语言服务和编辑器将使用文档数据对象相关联。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
-   创建您自己的快捷键，或通过设置使用的系统默认<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>对象显示属性。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 若要执行此操作，调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>属性。</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>  
  
     若要获得并使用非标准的键盘快捷方式，生成使用.vsct 文件。 有关详细信息，请参阅[Visual Studio 命令表 (。Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>如何使用编辑器工厂来获取核心编辑器  
 当实现核心编辑器编辑器工厂使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法中，执行显式承载一节中概述的所有步骤<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>文档数据对象<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>对象。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 若要显示的文本，获取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>接口从<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>对象，并调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 若要向编辑器中提供的语言服务，请调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法是在<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
 若要获取的快捷键，与上一节中，不同的默认您使用命令行上下文由<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法获取从核心编辑器时<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法将返回相同的命令 GUID 作为文本编辑器，核心编辑器的实例会自动获取默认的键盘快捷方式。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 有关一般信息，请参阅[演练︰ 创建核心编辑器和注册了编辑器中的文件类型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在核心编辑器](../extensibility/inside-the-core-editor.md)   
 [打开和保存项目项](../extensibility/internals/opening-and-saving-project-items.md)   
 [演练︰ 创建核心编辑器和注册了编辑器中的文件类型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
