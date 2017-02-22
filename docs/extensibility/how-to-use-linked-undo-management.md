---
title: "如何: 使用链接的撤消管理 | Microsoft Docs"
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
  - "编辑器 [Visual Studio SDK]，旧的链接的撤消管理"
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 使用链接的撤消管理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

链接撤消允许用户同时移除相同编辑在多个文件。  例如，同时文本在多个程序文件中更改，例如头文件， Visual C\+\+ 文件，是链接撤消事务。  链接撤消的内置功能撤消管理器环境的实现，因此， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> 用于操作此功能。  链接撤消由父实现取消可链接到单独取消视为唯一堆栈。抵消单位的单元。  方法为链接的使用以下部分中删除详细信息。  
  
### 对链接的使用撤消  
  
1.  缩放在 `SVsLinkedUndoManager` 访问的 `QueryService` 指向 `IVsLinkedUndoTransactionManager`。  
  
2.  创建初始父链接通过调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>抵消单位。  这将设置为起始点设置取消将分组的堆栈到链接撤消堆栈。  在 `OpenLinkedUndo` 方法还需要指定是否希望链接撤消是强名称或非强。  链接的非强取消行为意味着一些文档链接取消同级能关闭，并且仍然保留其他链接撤消其堆栈的同级节点。  严格的链接撤消行为将指定：所有链接的撤消同级堆栈要么全部一起撤消，要么一个都不得撤消。  添加链接的后续通过调用 [IOleUndoManager:: 添加](http://msdn.microsoft.com/library/windows/desktop/ms680135) 方法撤消堆栈。  
  
3.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> 回滚链接的所有抵消单位为一个。  
  
    > [!NOTE]
    >  为链接的实现撤消在编辑器中管理，添加取消管理。  有关链接的更多信息实现取消管理，请参见 [如何:实现取消管理](../extensibility/how-to-implement-undo-management.md)。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [如何: 实现撤消管理](../extensibility/how-to-implement-undo-management.md)