---
title: "如何： 使用链接的撤消管理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05e10305f7e4c243f799cfe33d4d9b86418eed86
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-linked-undo-management"></a>如何： 使用链接的撤消管理
链接的撤消后，用户可以同时撤消中多个文件相同的编辑。 例如，跨多个程序文件，如标头文件和 Visual c + + 文件，同时进行文本更改为链接的撤消事务。 链接的撤消功能内置于环境的撤消管理器中，实现和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>可以处理此功能。 链接的撤消由实现可以将链接在一起，以被视为单个撤消单元的单独撤消堆栈父撤消单元。 使用链接的撤消过程将在下一节中详细介绍。  
  
### <a name="to-use-linked-undo"></a>若要使用的链接的撤消  
  
1.  调用`QueryService`上`SVsLinkedUndoManager`以获取指向`IVsLinkedUndoTransactionManager`。  
  
2.  通过调用创建初始父链接的撤消单元<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>。 这将设置划分为链接的撤消堆栈的撤消堆栈的一组的起始点。 在`OpenLinkedUndo`还需要指定要链接的撤消要严格或非严格的方法。 非严格的链接的撤消行为意味着，某些文档的链接的撤消同级可以关闭并仍然保留的其他链接撤消其在堆栈上的同级。 严格的链接的撤消行为指定所有链接的撤消同级堆栈需要在一起或根本不能撤消。 添加后续的链接通过调用撤消堆栈[IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135)方法。  
  
3.  调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A>滚备份所有作为一个链接的撤消单元。  
  
    > [!NOTE]
    >  若要实现链接的撤消管理在编辑器中，添加撤消管理。 有关实现链接的撤消管理的详细信息，请参阅[如何： 实现撤消管理](../extensibility/how-to-implement-undo-management.md)。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [如何： 实现撤消管理](../extensibility/how-to-implement-undo-management.md)