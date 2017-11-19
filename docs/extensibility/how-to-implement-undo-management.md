---
title: "如何： 实现撤消管理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f61ee4c561e32f17afa1b53cbf3bd3bf982feeb4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-undo-management"></a>如何： 实现撤消管理
用于撤消管理的主要接口为<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>，由环境实现。 若要支持撤消管理，请实现单独撤消单元 (即， <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>，其中可以包含多个单独的步骤。  
  
 如何实现撤消管理根据你的编辑器是否支持多个视图，或不而异。 每个实现的过程进行详细介绍下列各节。  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>其中编辑器支持单个视图的情况下  
 在此方案中，编辑器不支持多个视图。 没有只有一个编辑器和一个文档，并且它们支持撤消。 使用以下过程来实现撤消管理。  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>若要支持单视图编辑器撤消管理  
  
1.  调用`QueryInterface`上`IServiceProvider`接口上的窗口框架`IOleUndoManager`，从要访问撤消管理器的文档视图对象 (`IID_IOLEUndoManager`)。  
  
2.  当视图被放置到窗口框架后时，它将获取站点指针，它可用于调用`QueryInterface`为`IServiceProvider`。  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>其中编辑器支持多个视图的情况下  
 如果你有文档和视图之间的分离，则通常一个撤消管理器与文档本身相关联。 所有撤消单元被都放置在与文档数据对象关联的一个撤消管理器。  
  
 而不是撤消管理器，其中提供了一个用于每个视图中，视图查询文档数据对象将调用<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>来实例化撤消管理器，指定 CLSID_OLEUndoManager 的类标识符。 OCUNDOID.h 文件中定义的类标识符。  
  
 使用时<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>若要创建您自己的撤消管理器实例，使用以下过程将撤消管理器挂钩到环境。  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>若要挂钩到环境的撤消管理器  
  
1.  调用`QueryInterface`从返回的对象上<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>为`IID_IOleUndoManager`。 存储指向<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>。  
  
2.  调用`QueryInterface`上`IOleUndoManager`为`IID_IOleCommandTarget`。 存储指向<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
3.  中继你<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>调入存储`IOleCommandTarget`接口下列 StandardCommandSet97 命令：  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  调用`QueryInterface`上`IOleUndoManager`为`IID_IVsChangeTrackingUndoManager`。 存储指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>。  
  
     使用指向指针<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>，和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A>方法。  
  
5.  调用`QueryInterface`上`IOleUndoManager`为`IID_IVsLinkCapableUndoManager`。  
  
6.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>与您的文档，其中应实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient>接口。 当文档关闭时，调用`IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`。  
  
7.  当文档关闭时，调用`QueryInterface`撤消管理器中为`IID_IVsLifetimeControlledObject`。  
  
8.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>。  
  
9. 当对文档进行更改时，调用<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>上的管理器`OleUndoUnit`类。 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>方法都会保留对引用对象，因此通常在发布其后直接<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>。  
  
 `OleUndoManager`类表示单个撤消堆栈实例。 因此，是每个跟踪的撤消或重做的数据实体的一个撤消管理器对象。  
  
> [!NOTE]
>  撤消管理器对象是广泛使用的文本编辑器，它是为文本编辑器没有特定支持的通用组件。 如果你想要支持多级撤消或重做，可以使用此对象进行管理。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [如何： 清除撤消堆栈](../extensibility/how-to-clear-the-undo-stack.md)