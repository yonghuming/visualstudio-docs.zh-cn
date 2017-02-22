---
title: "IDebugBoundBreakpoint2::SetCondition | Microsoft Docs"
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
  - "IDebugBoundBreakpoint2::SetCondition"
helpviewer_keywords: 
  - "SetCondition 方法"
  - "IDebugBoundBreakpoint2::SetCondition 方法"
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBoundBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

设置或更改该条件与此绑定断点。  
  
## 语法  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```c#  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### 参数  
 `bpCondition`  
 \[in\] 从描述条件的 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 枚举的值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  返回 `E_BP_DELETED` ，如果绑定断点对象的状态设置为 `BPS_DELETED` \(的一部分 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) 枚举\)。  
  
## 备注  
 以前与该断点的任何条件丢失。  
  
## 请参阅  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)