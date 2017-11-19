---
title: "保存自定义文档 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3cd6f5f45736a7b2578bc9df80a8472d3b50c3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="saving-a-custom-document"></a>保存自定义文档
环境句柄**保存**，**另存为**，和**保存所有**命令。 当用户单击**保存**，**另存为**，**或全部保存**上**文件**菜单或关闭解决方案，从而导致全部保存，以下进程时发生。  
  
 ![客户编辑器保存](../../extensibility/internals/media/private.gif "私有")  
保存，另存为和全部保存命令处理自定义编辑器  
  
 此过程详细介绍了以下步骤：  
  
1.  有关**保存**和**另存为**命令，该环境使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服务以确定活动文档窗口，因此应该因此保存项。 活动文档窗口了解后，环境查找的层次结构的指针和项标识符 (itemID) 中运行的文档表中的文档。 有关详细信息，请参阅[运行 Document 表](../../extensibility/internals/running-document-table.md)。  
  
     对于全部保存命令，环境使用信息正在运行的文档表中进行编译的所有项保存的列表。  
  
2.  当解决方案收到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>调用，它循环访问所选的项集的 (即，由公开多个选择<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服务)。  
  
3.  在所选内容的每个项，该解决方案使用层次结构指针来调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>方法来确定是否应启用保存菜单命令。 如果一个或多个项都已更新，则启用保存命令。 如果层次结构使用标准编辑器，然后查询的层次结构委托脏状态设置为编辑器中通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>方法。  
  
4.  于已更新每个所选项目，该解决方案使用层次结构指针来调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>适当的层次结构上的方法。  
  
     对于自定义编辑器中，文档数据对象和项目之间的通信是私有的。 因此，这两个对象之间处理任何特殊持久性问题。  
  
    > [!NOTE]
    >  如果你实现自己的持久性，一定要调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>方法以节省时间。 此方法检查以确保它是安全保存该文件 （例如，文件不是只读的）。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)