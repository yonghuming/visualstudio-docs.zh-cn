---
title: "运行模式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试引擎模式"
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 运行模式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下面是针对 IDE 会运行的三个架构，例如:  
  
-   [设计模式](#vsconoperationalmodesanchor1)  
  
-   [运行模式](#vsconoperationalmodesanchor2)  
  
-   [中断模式](#vsconoperationalmodesanchor3)  
  
 该自定义如何调试在这些模式之间的转换引擎 \(DE\)是要求您熟悉转换 framework 实现决定。  DE 可能存在也可能不直接实现这些方案。  这些模式实际上是调试开关根据用户操作或事件从 DE 的包架构。  例如，从中断模式的运行模式的转换是由 DE 的一个停止点的事件发起。  从转换中断到运行模式或步进模式由执行操作 \(如步骤的用户发起或执行。  有关 DE transitions 的更多信息，请参见 [控制执行](../../extensibility/debugger/control-of-execution.md)。  
  
##  <a name="vsconoperationalmodesanchor1"></a> 设计模式  
 ，在设置在应用程序中，的调试功能设计模式是调试 Visual Studio 非奔跑的状态。  
  
 在设计模式下，只有一些调试功能使用。  开发人员可以选择设置断点或创建监视表达式。  ， IDE 在设计模式下时， DE 从不加载或调用。  与 DE 的交互仅发生在运行的和中断模式下。  
  
##  <a name="vsconoperationalmodesanchor2"></a> 运行模式  
 ，当程序在 IDE，的调试会话中运行请运行模式发生。  应用程序运行，直到停止，直到命中断点时，或者，直到引发异常。  当应用程序运行到停止， DE transitions 为设计模式中。  当命中断点或引发异常， DE 中断模式的 transitions。  
  
##  <a name="vsconoperationalmodesanchor3"></a> 中断模式  
 ，在调试程序的执行挂起时，中断模式时发生。  处于中断时中断模式提供开发人员应用程序的快照并允许开发人员分析应用程序的状态和更改应用程序的运行方式。  开发人员可以查看，并编辑代码，检查或修改数据，重新启动应用程序，结束执行或继续从相同的执行点。  
  
 ，当 DE 发送一个同步终止的事件时，中断模式中输入。  同步终止的事件，也称为停止事件，通知会话调试管理器 \(SDM\)和 IDE 正在调试的应用程序停止执行代码。  [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 和 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 接口是停止事件的示例。  
  
 停止事件通过调用继续到下列方法之一，从转换中断模式运行的或步进模式的调试器:  
  
-   [执行](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [单步执行](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [继续](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> 步进模式  
 步进模式时，会发生操作步骤到下一行代码，或者为，在中，或在函数之外中。  逐句通过调用方法来 [单步执行](../../extensibility/debugger/reference/idebugprocess3-step.md)。  此方法要求 `DWORD`指定 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) 和 [STEPKIND](../../extensibility/debugger/reference/stepkind.md) 枚举作为输入参数的。  
  
 当程序成功单步执行到下一行代码或功能中，也运行到光标或设置断点，回中断模式的自动、转换。  
  
## 请参阅  
 [控制执行](../../extensibility/debugger/control-of-execution.md)