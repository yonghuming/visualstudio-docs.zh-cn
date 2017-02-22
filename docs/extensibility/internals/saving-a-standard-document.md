---
title: "保存标准文档 | Microsoft Docs"
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
  - "编辑器 [Visual Studio SDK]，保存的标准文档"
  - "项目 [Visual Studio SDK]，保存的标准文档"
  - "持久性、 保存的标准文档"
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 保存标准文档
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

环境处理保存，保存，并保存所有命令。  当用户选择 **保存**、 **保存**或 **" 全部保存** 从 **文件** 菜单或关闭解决方案，使 **" 全部保存**，下面的过程中发生。  
  
 ![标准编辑器](../../extensibility/internals/media/public.png "Public")  
保存，保存，并保存过程与标准编辑的所有命令  
  
 这将在下面的过程的步骤详细信息:  
  
1.  当 **保存** 和 **保存** 命令时，该环境使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服务来确定活动文档窗口，因此应保存的项。  有效文档窗口知道，该环境查找层次结构指针和项 ID \(itemID\) 在运行的文档的文档表。  有关更多信息，请参见 [正在运行的 Document 表](../../extensibility/internals/running-document-table.md)。  
  
     当 **" 全部保存** 命令时，环境将处于正在运行的信息文档表生成所有项目列表保存。  
  
2.  在解决方法接收 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 调用时，它通过重复设置选定的项 \(即 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服务公开的多重选择\)。  
  
3.  在选定内容每个项目，解决方案使用层次结构指针调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 方法确定是否应启用 **Save** 菜单命令。  一个或多个项目不正确，则 **Save** 命令有效。  如果该层次结构使用标准编辑，则该层次结构委托查询错误的状态到编辑器通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 方法。  
  
4.  在不正确的每个选定的项目，解决方案使用层次结构指针调用适当的层次结构中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 方法。  
  
     通常会使该层次结构可以使用标准编辑器编辑文档。  在这种情况下，该编辑的文档数据对象应支持 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 接口。  在收到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 方法之后调用，该项目应通知文档通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> 方法保存文档中数据对象的编辑器。  编辑器可以提供为处理 **保存** 对话框，通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 接口的 `Query Service` 。  这将返回指向 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 接口。  编辑器必须然后调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> 方法，并传递指向编辑的 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 实现通过 `pPersistFile` 参数。  该环境然后执行保存操作并为编辑器提供 **保存** 对话框。  该环境然后调用返回与 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>的编辑器。  
  
5.  如果用户尝试保存没有权限文档 \(即以前未保存文档\)，则为命令的保存实际上执行。  
  
6.  以命令的保存，环境显示另存为 " 对话框，提示文件名的用户。  
  
     如果文件的名称更改为，则该层次结构来更新文档框架的缓存信息负责通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>\(VSFPROPID\_MkDocument\)。  
  
 如果 **保存** " 命令将文档的位置，因此，该层次结构对文件位置区分大小，则该层次结构传递给负责所有权打开文档窗口到另一个层次结构。  例如，则发生，如果项目跟踪文件是否是内部或外部文件 \(杂项文件\) 有关项目。  使用下面的过程中更改文件的所有权更改为杂项文件项目。  
  
## 更改文件的所有权  
  
#### 向杂项文件的更改文件的所有权项目  
  
1.  查询 <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> 接口的服务。  
  
     为 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> 的指针返回。  
  
2.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> \(`pszMkDocumentNew`， `punkWindowFrame`\) 方法调用文档到新的层次结构。  执行保存该层次结构作为命令调用此方法。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)