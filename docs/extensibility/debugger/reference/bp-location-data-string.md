---
title: "BP_LOCATION_DATA_STRING | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_DATA_STRING"
helpviewer_keywords: 
  - "BP_LOCATION_DATA_STRING 结构"
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用于设置基于字符串用户可以从集成开发环境 \(ide\) 中输入的数据断点 \(IDE\)。  
  
## 语法  
  
```cpp#  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## 成员  
 `pThread`  
 表示线程断点发生的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象。  
  
 `bstrContext`  
 断点的上下文在代码中，通常一个方法或函数名如下所示调用堆栈。  
  
 `bstrDataExpr`  
 数据字符串用户输入设置断点。  
  
 `dwNumElements`  
 元素数在断点处得到的数据的字符串。  
  
## 备注  
 作为一个联合的一部分，此结构是 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 结构的成员。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)