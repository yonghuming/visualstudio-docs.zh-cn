---
title: "IDebugPendingBreakpoint2::Bind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::Bind"
helpviewer_keywords: 
  - "Bind 方法"
  - "IDebugPendingBreakpoint2::Bind 方法"
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPendingBreakpoint2::Bind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

将此挂起的断点到一个或多个代码位置。  
  
## 语法  
  
```cpp#  
HRESULT Bind(   
   void   
);  
```  
  
```c#  
int Bind();  
```  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  ，如果断点删除，返回 `E_BP_DELETED` 。  
  
## 备注  
 当调用此方法时，调试引擎 \(DE\)应尝试将此挂起的断点到匹配的所有代码位置。  
  
 此方法返回后，调用方需要等待分别指示的事件挂起的断点绑定或错误。假定之前调用 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) 或 [EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md).methods 将枚举所有区域或错误，断点。  
  
## 请参阅  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)