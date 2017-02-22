---
title: "如何: 实现撤消管理 | Microsoft Docs"
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
  - "编辑器 [Visual Studio SDK]，旧的撤消管理"
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 实现撤消管理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

主要接口用于取消管理是 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>，由环境实现。  若要支持取消管理，单独的实现抵消单位 \(即 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>，可以包含多个单独的步骤。  
  
 如何实现取消管理取决于是否编辑器支持多个视图。  每个实现的程序在下一节详细描述。  
  
## 用例编辑支持单个视图的位置  
 在此方案中，编辑器不支持多视图。  只有一个编辑器，另一个用于文档，并且，它们支持取消。  使用以下过程实现取消管理。  
  
#### 若要支持取消单视图编辑器的管理  
  
1.  调用 `IServiceProvider` 接口的 `QueryInterface` 在 `IOleUndoManager`的窗口框架组成，通常从文档视图对象访问取消管理器 \(`IID_IOLEUndoManager`\)。  
  
2.  在视图放置到窗架时，它会获取该站点指针，它可以使用调用 `IServiceProvider`的 `QueryInterface` 。  
  
## 用例编辑支持多个视图的位置  
 如果您有文档和视图分开，则通常有一个取消管理器与文档。  所有在一个抵消单位放置取消管理器与文档数据对象。  
  
 而不是查询移除管理器的视图中，的每个视图的文档时，数据对象调用 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 实例化取消管理器中，指定 CLSID\_OLEUndoManager 类标识符。  类标识符在 OCUNDOID.h 文件中定义的。  
  
 当使用 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 创建时自己取消管理器实例，请使用下面的过程将取消管理器到环境。  
  
#### 将取消管理器到环境  
  
1.  调用从 `IID_IOleUndoManager`的 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> 返回的对象的 `QueryInterface` 。  存储指向 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>。  
  
2.  调用 `IOleUndoManager` 的 `QueryInterface``IID_IOleCommandTarget`的。  存储指向 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
3.  出现 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 和 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 调入存储的 `IOleCommandTarget` 下面 StandardCommandSet97 命令的接口:  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  调用 `IOleUndoManager` 的 `QueryInterface``IID_IVsChangeTrackingUndoManager`的。  存储指向 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>。  
  
     使用指针 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> 调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> 方法。  
  
5.  调用 `IOleUndoManager` 的 `QueryInterface``IID_IVsLinkCapableUndoManager`的。  
  
6.  调用与文档的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> ，还应实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> 接口。  关闭文档后，请调用 `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`。  
  
7.  关闭文档后，调用在撤消管理器的 `QueryInterface``IID_IVsLifetimeControlledObject`的。  
  
8.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>。  
  
9. 当更改文档时，调用管理器的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> 具有 `OleUndoUnit` 类的。  <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> 方法保持对对象，因此您通常释放它在 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>之后。  
  
 `OleUndoManager` 类表示单个撤消堆栈实例。  因此，具有移除对象每个数据实体跟踪提供取消的经理或重做操作。  
  
> [!NOTE]
>  在文本编辑器中广泛使用取消管理器对象，它是没有特定于文本编辑器支持的泛型元素。  如果要支持多级撤消或重做操作，您可以使用此对象来实现。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [如何: 清除撤消堆栈](../extensibility/how-to-clear-the-undo-stack.md)