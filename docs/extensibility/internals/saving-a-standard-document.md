---
title: "保存标准文档 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73ef7f1b347dc2fdcfe2904ef19a2d52036d927e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="saving-a-standard-document"></a>保存标准文档
环境处理保存、 另存为，和保存所有命令。 当用户选择**保存**，**另存为**，或**保存所有**从**文件**菜单或关闭解决方案，从而导致**保存所有**，将发生以下过程。  
  
 ![标准编辑器](../../extensibility/internals/media/public.gif "公共")  
保存，另存为和全部保存命令处理的标准编辑器  
  
 此过程详细介绍了以下步骤：  
  
1.  当**保存**和**另存为**命令当选中时，该环境使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服务以确定活动文档窗口，因此应该因此保存项。 活动文档窗口了解后，环境查找的层次结构的指针和项标识符 (itemID) 中运行的文档表中的文档。 有关详细信息，请参阅[运行 Document 表](../../extensibility/internals/running-document-table.md)。  
  
     当**保存所有**选择命令，环境使用正在运行的 document 表中的信息进行编译的所有项保存的列表。  
  
2.  当解决方案收到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>调用，它循环访问所选的项集的 (即，由公开多个选择<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服务)。  
  
3.  在所选内容的每个项，该解决方案使用层次结构指针来调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>方法来确定是否**保存**应启用菜单命令。 如果一个或多个项已更新，则**保存**启用命令。 如果层次结构使用标准编辑器，然后查询的层次结构委托脏状态设置为编辑器中通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>方法。  
  
4.  于已更新每个所选项目，该解决方案使用层次结构指针来调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>适当的层次结构上的方法。  
  
     很常见的层次结构，可以使用标准编辑器来编辑该文档。 在这种情况下，文档数据对象应支持该编辑器<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>接口。 在接收时<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>方法调用，该项目应通知的编辑器中保存文档后通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A>文档数据对象上的方法。 编辑器可以允许处理环境**另存为**对话框中，通过调用`Query Service`为<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>接口。 这将返回一个指向<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>接口。 然后必须调用编辑器<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>方法，将指针传递到编辑器的<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>通过实现`pPersistFile`参数。 环境，然后执行保存操作并提供**另存为**编辑器对话框。 环境然后回拨到编辑器中，与<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>。  
  
5.  如果该用户尝试保存一个未命名的文档 （即，以前未保存的文档），则实际执行的另存为命令。  
  
6.  对于另存为命令，环境将显示另存为对话框中，提示用户输入文件名称。  
  
     如果已更改文件的名称，则层次结构负责更新文档帧的缓存信息通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument)。  
  
 如果**另存为**命令将移动文档的位置，并且层次结构是敏感的文档位置，则层次结构负责关闭打开的文档窗口的所有权交给另一个层次结构。 例如，这样如果项目跟踪文件是否为内部或外部的文件 （杂项文件） 与项目之间的关系。 使用以下过程更改为杂项文件项目的文件的所有权。  
  
## <a name="changing-file-ownership"></a>更改文件所有权  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>若要将文件所有权更改为杂项文件项目  
  
1.  查询服务<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>接口。  
  
     指向的指针<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>返回。  
  
2.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A>(`pszMkDocumentNew`， `punkWindowFrame`) 方法传输到新层次结构的文档。 层次结构执行的另存为命令调用此方法。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [打开和保存项目项](../../extensibility/internals/opening-and-saving-project-items.md)