---
title: "运行模式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 205837bc5bfdf9476839ea1e54a53dc57dbf9a72
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="operational-modes"></a>运行模式
有三种模式在其中 IDE 可以操作，如下所示：  
  
-   [设计模式](#vsconoperationalmodesanchor1)  
  
-   [运行模式](#vsconoperationalmodesanchor2)  
  
-   [中断模式](#vsconoperationalmodesanchor3)  
  
 你自定义调试引擎 (DE) 这些模式之间进行过渡的方式是一个实现决策，要求你熟悉的转换机制。 DE 可能或可能不直接实现这些模式。 这些模式实际上调试包模式切换基于用户执行任何操作或从 DE 的事件。 例如，从运行模式下为中断模式的转换是通过 DE 中的停止事件引发。 从中断，或者模式或步骤模式的转换是由用户执行操作，如单步执行或执行引发。 有关 DE 转换的详细信息，请参阅[控制执行](../../extensibility/debugger/control-of-execution.md)。  
  
##  <a name="vsconoperationalmodesanchor1"></a>设计模式  
 设计模式是 nonrunning 状态的 Visual Studio 调试时，在这段时间可以设置调试应用程序中的功能。  
  
 只有几个调试在设计模式下使用功能。 开发人员可以选择设置断点，或创建监视表达式。 DE 永远不会加载服务说明或调用 IDE 处于设计模式时。 与 DE 交互过程中发生运行和中断模式。  
  
##  <a name="vsconoperationalmodesanchor2"></a>运行模式  
 在 IDE 中调试会话中运行程序时，会出现运行的模式。 应用程序运行，直到为止终止，直到命中断点，或直到引发异常。 当应用程序运行时终止，到设计模式下的 DE 转换。 当命中断点或引发异常时，DE 转换为中断模式。  
  
##  <a name="vsconoperationalmodesanchor3"></a>中断模式  
 当执行调试程序被挂起时，会出现中断模式。 中断模式下提供开发人员的中断时间上的应用程序的快照，并允许开发人员可以分析应用程序的状态更改应用程序将运行方式。 开发人员可以查看和编辑代码、 检查或修改数据、 重新启动应用程序、 结束执行，或继续执行从相同的点。  
  
 DE 发送同步 stopping 事件，则会进入中断模式。 同步停止事件，也称为停止事件通知会话调试管理器 (SDM) 和正在调试的应用程序已停止执行代码 IDE。 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)接口是停止事件的示例。  
  
 正在停止事件是通过调用以下方法，转换调试器在中断模式下才能运行或单步模式之一 （续）：  
  
-   [执行](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a>步执行模式  
 当程序执行到下一行的代码，或执行、 逐过程执行或跳出函数时，会出现步骤模式。 通过调用该方法执行一个步骤[步骤](../../extensibility/debugger/reference/idebugprocess3-step.md)。 此方法要求`DWORD`指定的 s [STEPUNIT](../../extensibility/debugger/reference/stepunit.md)和[STEPKIND](../../extensibility/debugger/reference/stepkind.md)作为输入参数的枚举。  
  
 如果程序已成功将单步到下一行代码或执行某一函数，或运行到光标处或设置断点，DE 将自动转换回为中断模式。  
  
## <a name="see-also"></a>另请参阅  
 [控制执行](../../extensibility/debugger/control-of-execution.md)