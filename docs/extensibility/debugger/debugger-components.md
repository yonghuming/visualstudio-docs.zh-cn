---
title: "调试程序组件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [Visual Studio] 组件"
  - "调试组件 [Visual Studio SDK]"
  - "调试 [调试 SDK]，组件"
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# 调试程序组件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调试器可作为 VSPackage 和管理整个调试会话。  调试会话包含以下元素:  
  
-   **调试包:** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调试器提供相同的用户界面，无论进行调试。  
  
-   **会话调试管理器 \(SDM\):** 提供一致的编程接口。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调试器能够管理各种调试引擎。  它由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]实现。  
  
-   **过程调试管理器 \(PDM\):** 为 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]所有正在运行的实例管理，，可以是或正在调试所有程序的列表。  它由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]实现。  
  
-   **调试引擎 \(DE\):** 为监视正在调试，将运行的过程的状态为 SDM 和 PDM 的程序负责和与表达式计算器和符号提供程序提供对程序的内存和变量的状态的实时分析。  它通过它支持\) 若要支持它们的运行时的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(对于语言和第三方供应商实现。  
  
-   **表达式计算器 \(EE\):** 提供对动态计算的变量支持，并且用户提供的表达式，当程序终止了在特定时点。  它通过它支持\) 若要支持这些语言的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(对于语言和第三方供应商实现。  
  
-   **符号 \(SP\)提供程序:** 并调用符号处理程序，映射程序的调试符号至程序的正在运行的实例，以便提供有意义的信息 \(例如源代码级调试和表达式计算\)。  它实现由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(对于公共语言运行时 \[\] CLR 符号和程序数据库 \[\] PDB 符号文件格式\) 和由具有存储调试信息它们的所有权方法的第三方供应商联系。  
  
 下面的关系图显示了 Visual Studio 调试器中这些元素的关系。  
  
 ![调试组件概述](../../extensibility/debugger/media/dbugcompovrview.png "DBugCompOvrview")  
  
## 本节内容  
 [调试包](../../extensibility/debugger/debug-package.md)  
 讨论调试包，在 UI 中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell 和处理所有运行。  
  
 [进程调试管理器](../../extensibility/debugger/process-debug-manager.md)  
 提供 PDM 的功能的概述，作为经理的进程进行调试。  
  
 [会话调试管理器](../../extensibility/debugger/session-debug-manager.md)  
 定义 SDM，提供调试会话一个统一的视图对 IDE。  SDM 管理 DE。  
  
 [调试引擎](../../extensibility/debugger/debug-engine.md)  
 文档、提供的调试服务。  
  
 [运行模式](../../extensibility/debugger/operational-modes.md)  
 提供 IDE 会运行三个模式的概述:设计模式，运行模式，并中断模式。  转换 framework 还讨论。  
  
 [表达式计算器](../../extensibility/debugger/expression-evaluator.md)  
 解释 EE 的目的在运行时。  
  
 [符号提供程序](../../extensibility/debugger/symbol-provider.md)  
 讨论，在实现，符号提供程序如何计算变量与表达式。  
  
 [类型的可视化工具和自定义查看器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 讨论如何类型可视化工具和自定义浏览器是，以及角色表达式计算器在支持模拟两个。  
  
## 相关章节  
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要调试体系结构概念。  
  
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)  
 解释、如何在代码、文档和表达式计算上下文中同时运行。  支持三种上下文、位置、位置或计算都描述，与之相关。  
  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)  
 包含指向各种调试任务，如启动程序并计算表达式。  
  
## 请参阅  
 [入门](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)