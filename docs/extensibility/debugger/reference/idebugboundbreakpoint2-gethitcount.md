---
title: "IDebugBoundBreakpoint2::GetHitCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetHitCount"
helpviewer_keywords: 
  - "GetHitCount 方法"
  - "IDebugBoundBreakpoint2::GetHitCount 方法"
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::GetHitCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取此绑定断点的当前命中次数。  
  
## 语法  
  
```cpp#  
HRESULT GetHitCount(   
   DWORD* pdwHitCount  
);  
```  
  
```c#  
int GetHitCount(   
   out uint pdwHitCount  
);  
```  
  
#### 参数  
 `pdwHitCount`  
 \[out\] 返回命中次数。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  返回 `E_BP_DELETED` ，如果绑定断点对象的状态设置为 `BPS_DELETED` \(的一部分 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) 枚举\)。  
  
## 备注  
 命中次数是该断点激发的是当前过程中运行该会话的次数。  
  
## 请参阅  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)