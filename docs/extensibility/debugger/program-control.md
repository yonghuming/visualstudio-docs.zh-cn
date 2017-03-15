---
title: "程序控制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，控制执行"
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 程序控制
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在调试的 Visual Studio，以下所有步骤的和延续的实例中发生在过程级别:  
  
-   设置下一语句，也就是说，设置计算机到下一条指令是在特定框架环境中  
  
-   执行，即，在退出在单步模式外部  
  
-   单步执行到下命令  
  
-   继续当前单步模式  
  
-   挂起程序包含的线程  
  
-   还原程序包含的线程  
  
> [!NOTE]
>  查看调用堆栈在线程级别上实现。  枚举帧信息，请查看线程的调用堆栈，必须执行 [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 接口的所有方法时。  
  
## 程序控件的方法  
 下表显示必须为最低限度上函数执行调试引擎 \(DE\)和执行控制 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 的方法。  
  
|方法|说明|  
|--------|--------|  
|[IDebugProgram2:: 执行](../../extensibility/debugger/reference/idebugprogram2-execute.md)|继续运行从一种停止状态的程序包含的所有线程。  对执行控件。|  
|[IDebugProgram2:: 继续](../../extensibility/debugger/reference/idebugprogram2-continue.md)|继续运行从一种停止状态的程序包含的所有线程。  对执行控件。|  
|[IDebugProgram2:: 步骤](../../extensibility/debugger/reference/idebugprogram2-step.md)|执行在特定线程上一个步骤。  继续运行程序包含的其他线程。  对执行控件。|  
  
 对于多线程程序中，还必须执行 [IDebugProgram2:: EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 方法和 [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) 接口的所有方法。  
  
## 请参阅  
 [执行控制和状态评估](../../extensibility/debugger/execution-control-and-state-evaluation.md)