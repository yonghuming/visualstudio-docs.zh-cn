---
title: "IEnumDebugThreads2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugThreads2"
helpviewer_keywords: 
  - "IEnumDebugThreads2"
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此 interfac 枚举运行在当前线程调试会话。  
  
## 语法  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## 实现者说明  
 调试引擎 \(DE\)实现此接口表示线程列表程序中的。  
  
## 调用方的说明  
 调用 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) 获取表示任何线程的列表在运行进程的所有过程的此接口。  调用 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 获取表示线程的列表此接口上运行的程序。  
  
## 方法按 Vtable 顺序  
 下表显示 `IEnumDebugThreads2`方法。  
  
|方法|说明|  
|--------|--------|  
|[下一步](../Topic/IEnumDebugThreads2::Next.md)|检索线程指定数目的枚举序列的。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|跳过线程指定数目的枚举序列的。|  
|[重置](../Topic/IEnumDebugThreads2::Reset.md)|重置枚举序列与开头。|  
|[克隆](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|创建包含枚举状态和当前一个相同的枚举数。|  
|[GetCount](../Topic/IEnumDebugThreads2::GetCount.md)|获取线程数在枚举数。|  
  
## 备注  
 Visual Studio 通常获取此接口更新 **线程** 窗口和获取列表中的第一个线程，以调用 [执行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)、 [继续](../../../extensibility/debugger/reference/idebugprocess3-continue.md)和 [单步执行](../../../extensibility/debugger/reference/idebugprocess3-step.md)。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [单步执行](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [继续](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [执行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)