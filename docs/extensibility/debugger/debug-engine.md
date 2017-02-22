---
title: "调试引擎 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试引擎"
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 调试引擎
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调试引擎 \(DE\)与解释器或操作系统使用提供调试服务 \(如执行控件、断点和表达式计算。  DE 为监视正在调试的程序的状态负责。  若要执行此操作，请完成、使用任何方法将它适用于支持的运行时，是否从 CPU 或从运行时提供的 API。  
  
 例如，公共语言运行 \(CLR\)时提供框架通过 ICorDebugXXX 接口监视正在运行的程序。  支持 CLR 的 DE 使用适当的 ICorDebugXXX 接口记录中调试托管代码程序。  然后将所有状态更改为会话调试管理器 \(SDM\)，则为 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 这样的信息。  
  
> [!NOTE]
>  调试引擎面向特定运行时，也就是说，正在调试的程序在运行的系统。  CLR 是托管代码的运行时，因此， Win32 运行时用于本机 windows 应用程序。  如果您创建的语言可以将这两个运行时之一， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 已提供必要调试引擎。  您必须实现的任何是表达式计算器。  
  
## 调试引擎操作  
 监视服务通过 DE interfaces 实现，并可能导致调试包若要在不同操作状态之间的转换。  有关更多信息，请参见 [运行模式](../../extensibility/debugger/operational-modes.md)。  通常只有每个运行时环境的一 DE implementation。  
  
> [!NOTE]
>  当具有 Transact\-SQL 的单独 DE implementations 和 [!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)]时， VBScript 和 [!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)] 共享单个 DE。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调试启用调试引擎运行两种方式之一:或在同一进程作为 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell，或者在同一进程，当在中调试对象的程序。  后一种形式通常发生，当正在调试的进程实际上是运行在解释器下的脚本，因此，调试引擎必须具有解释器中精湛的知识来监视该脚本。  请注意，在这种情况下，解释器实际上是运行时;调试引擎是为特定运行时实现。  此外，唯一 DE 的实现中拆分进程和计算机边界 \(例如，远程调试\)。  
  
 DE 显示调试接口的  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  所有通信是通过 COM。  DE 是否加载进程，进程外，否则在另一台计算机，它不会影响组件通信。  
  
 DE 与表达式计算器使用组件使该特定运行时的 DE 可以了解表达式语法。  DE 还使用符号处理程序元素处理不同符号调试信息的语言编译器生成的访问。  有关更多信息，请参见[表达式计算器](../../extensibility/debugger/expression-evaluator.md)和 [符号提供程序](../../extensibility/debugger/symbol-provider.md)。  
  
## 请参阅  
 [调试程序组件](../../extensibility/debugger/debugger-components.md)   
 [表达式计算器](../../extensibility/debugger/expression-evaluator.md)   
 [符号提供程序](../../extensibility/debugger/symbol-provider.md)