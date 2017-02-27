---
title: "堆栈帧 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "堆栈帧调试"
  - "调试 [调试 SDK]，堆栈帧"
  - "堆栈帧"
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 堆栈帧
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

根据调试器体系结构， **堆栈帧**:  
  
-   是提供线程的执行上下文堆栈的抽象。  线程在函数内始终执行。  堆栈帧包含该函数的局部变量和参数传递给它。  为了用 Visual Studio 调试，所调试的语言或环境必须支持堆栈帧。  
  
-   标识和自我描述，并且可以返回关联的线程。  堆栈帧也能返回表示当前指令指针的代码上下文，以及关联的文档和表达式计算上下文。  
  
-   具有描述局部变量和参数的名称、类型和值，并在各种 IDE 显示调试窗口的属性。  
  
-   由 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 接口表示，通常创建的调试引擎 \(DE\)或虚拟机作为执行线程结果。  
  
## 请参阅  
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)