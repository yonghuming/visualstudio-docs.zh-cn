---
title: "IDebugExpressionContext2 | Microsoft Docs"
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
  - "IDebugExpressionContext2"
helpviewer_keywords: 
  - "IDebugExpressionContext2 接口"
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示表达式计算的上下文  
  
## 语法  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示可以在其中计算表达式的上下文。  
  
## 调用方的说明  
 为 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 的调用返回此接口。  此接口可访问，仅当正在调试的程序暂停，而堆栈帧可用。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugExpressionContext2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetName](../Topic/IDebugExpressionContext2::GetName.md)|检索计算上下文的名称。|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|分析计算的基于文本的表达式。|  
  
## 备注  
 计算上下文可视为执行的表达式计算范围。  
  
 当程序暂停后，该会话调试管理器 \(SDM\)从 DE 的一个堆栈帧的调用。 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。  SDM 然后调用 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 获取 `IDebugExpressionContext2` 接口。  这通过对 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 的调用执行创建 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 接口，表示准备已分析的计算表达式。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)