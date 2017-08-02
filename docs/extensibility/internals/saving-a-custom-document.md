---
title: "保存自定义文档 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "持久性、 保存自定义文档"
  - "项目 [Visual Studio SDK]，保存自定义文档"
  - "编辑器 [Visual Studio SDK]，保存自定义文档"
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 保存自定义文档
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

环境处理 **Save**、 **Save As**和 **Save All** 命令。  当用户单击 **保存**时， **保存**，在 **文件** 菜单的 **或者全部保存** 或关闭解决方案，从而导致保存整个，下面的过程将。  
  
 ![客户编辑器中的“保存”](~/docs/extensibility/internals/media/private.gif "Private")  
保存，保存，并保存正在为自定义编辑器的所有命令  
  
 这将在下面的过程的步骤详细信息:  
  
1.  为 **保存** 和 **保存** 命令，环境使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服务来确定活动文档窗口，因此应保存的项。  有效文档窗口知道，该环境查找层次结构指针和项 ID \(itemID\) 在运行的文档的文档表。  有关更多信息，请参见 [正在运行的 Document 表](../../extensibility/internals/running-document-table.md)。  
  
     对于保存所有命令，环境将处于正在运行的信息文档表生成所有项目列表保存。  
  
2.  在解决方法接收 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 调用时，它通过重复设置选定的项 \(即 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服务公开的多重选择\)。  
  
3.  在选定内容每个项目，解决方案使用层次结构指针调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 方法确定是否应启用保存菜单命令。  一个或多个项目是错误的，则保存命令有效。  如果该层次结构使用标准编辑，则该层次结构委托查询错误的状态到编辑器通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 方法。  
  
4.  在不正确的每个选定的项目，解决方案使用层次结构指针调用适当的层次结构中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 方法。  
  
     对于自定义编辑器，文档数据对象和项目之间的通信是私有的。  因此，任何特定持久性问题已处理在这两个对象之间。  
  
    > [!NOTE]
    >  如果实现拥有持久性，请务必调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 方法以节省时间。  此方法检查，以确保是安全的保存文件 \(例如，文件不是只读的。\)  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)