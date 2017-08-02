---
title: "支持多个文档视图 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，自定义的多个文档视图"
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 支持多个文档视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以提供多个文档的视图通过创建单独的文档数据和文档编辑器的视图对象。  附加文档视图的情形是有用的是:  
  
-   新窗口支持:您希望此编辑器提供了相同类型的两个或多个视图，因此，已经打开一个窗口在编辑器的用户可以通过选择 **新窗口** 命令打开一个新窗口从 **窗口** 菜单。  
  
-   窗体和代码视图支持:您希望此编辑器提供了不同类型的视图。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，例如，提供一个窗体视图和一个代码视图。  
  
 有关这方面的更多信息，请参见。 EditorFactory.cs 文件的 CreateEditorInstance 程序在 Visual Studio 包模板创建的自定义编辑项目。  有关此项目的更多信息，请参见 [演练: 创建自定义编辑器](../extensibility/walkthrough-creating-a-custom-editor.md)。  
  
## 同步视图  
 在实现多个视图时，文档数据对象以使所有视图负责与数据同步。  您可以使用过程在 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 的事件接口与数据同步多个视图。  
  
 如果不使用 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 对象同步多个视图，则必须实现拥有事件系统对组成其进行处理到文档的数据对象。  可以使用粒度的不同级别保持多个视图是最新的。  设置最大，粒度，因为您输入一个视图能够立即更新其他视图。  最小的粒度，其他视图不更新，直到激活它们。  
  
## 确定是否文档已打开的数据  
 运行文档在集成开发环境帮助 \(IDE\)跟踪的表 \(RDT\)数据。文档是否已打开，则，如下图所示。  
  
 ![DocDataView 图](~/docs/extensibility/media/docdataview.gif "Docdataview")  
多个视图  
  
 默认情况下，每个视图 \(文档视图对象\) 在其自己的窗架 \(<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>\) 包含。  如已经注意到，但是，文档数据可以显示在多个视图。  若要实现此功能， Visual Studio 检查 RDT 确定相关的文档是否已打开在编辑器中  当 IDE 调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 创建编辑器时，在 `punkDocDataExisting` 参数返回的非空值指示文档已打开的在其他编辑器。  有关 RDT 方式的更多信息函数，请参见 [正在运行的 Document 表](../extensibility/internals/running-document-table.md)。  
  
 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 实现，请检查在 `punkDocDataExisting` 返回的文档数据对象确定文档是否为编辑器正确。  \(例如，应由 HTML 编辑器仅显示 HTML 数据。\)如果适用，则编辑工厂应为数据提供第二个视图。  如果 `punkDocDataExisting` 参数不是 `NULL`，可能会文档数据对象已在其他编辑器中其中之一，或者，更可能，文档数据已打开的与相同的不同视图编辑器。  如果文档数据已在编辑工厂不支持的其他编辑器， Visual Studio 无法打开编辑工厂。  有关更多信息，请参见 [如何︰ 附加视图文档数据](../extensibility/how-to-attach-views-to-document-data.md)。