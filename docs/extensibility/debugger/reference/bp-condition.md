---
title: "BP_CONDITION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_CONDITION"
helpviewer_keywords: 
  - "BP_CONDITION 结构"
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_CONDITION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述断点激发的条件。  
  
## 语法  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```c#  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## 成员  
 `pThread`  
 表示应用程序的活动线程包含断点的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象。  
  
 `styleCondition`  
 从描述该断点条件的样式 [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) 枚举的值。  
  
 `bstrContext`  
 断点的位置。  
  
 `bstrCondition`  
 断点的激发条件。  
  
 `nRadix`  
 用于计算任何数值信息基数。  
  
## 备注  
 此结构是 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 和 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 结构的成员。  
  
 此结构参数形式传递给 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) 和 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) 方法。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)