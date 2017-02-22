---
title: "IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "SetPassCount 方法"
  - "IDebugPendingBreakpoint2::SetPassCount 方法"
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

设置或更改通过计数与挂起的断点。  
  
## 语法  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### 参数  
 `bpPassCount`  
 \[in\] 包含通过计数的 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 结构。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  ，如果断点删除，返回 `E_BP_DELETED` 。  
  
## 备注  
 以前与挂起的断点的所有通过计数丢失。  从此挂起的断点绑定的所有调用设置断点设置其通过计数到 `bpPassCount` 参数。  
  
## 请参阅  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)