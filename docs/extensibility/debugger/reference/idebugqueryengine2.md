---
title: "IDebugQueryEngine2 | Microsoft Docs"
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
  - "IDebugQueryEngine2"
helpviewer_keywords: 
  - "IDebugQueryEngine2 接口"
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口允许会议调试管理器 \(SDM\)检索表示调试引擎 \(DE\)的接口。  
  
## 语法  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## 实现者说明  
 DE implements 在实现最常见的、 interfaces 对象的此接口 \(例如 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)、 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)和 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\) 来允许访问、 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 接口的访问。  
  
## 调用方的说明  
 调用在典型的、 interface 的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugQueryEngine2`方法。  
  
|方法|说明|  
|--------|--------|  
|[GetEngineInterface](../Topic/IDebugQueryEngine2::GetEngineInterface.md)|获取自定义调试引擎 \(DE\)接口。|  
  
## 备注  
 此接口在对象通常实现 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 实现接口以便支持通过功能因果关系顺序的步骤;也就是说，当调试器单步执行函数外时，执行的下一个函数不能完全位于堆栈以前的功能，而在另一个线程的函数。  有关 “因果关系的定义，请参见 [Visual Studio 调试器术语表](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)