---
title: "如何: 清除撤消堆栈 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的清除撤消堆栈"
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 如何: 清除撤消堆栈
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在下面的过程说明如何清除撤消堆栈。  
  
### 清除撤消堆栈  
  
1.  清除撤消堆栈使用 [IOleUndoManager:: DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) 方法。  下面是此操作的示例:  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## 请参阅  
 [如何: 实现撤消管理](../extensibility/how-to-implement-undo-management.md)