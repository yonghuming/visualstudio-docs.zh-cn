---
title: "创建自定义调试引擎 | Microsoft Docs"
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
  - "调试引擎实现"
  - "调试引擎，自定义"
  - "调试 [调试 SDK]，自定义调试引擎"
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 创建自定义调试引擎
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

调试引擎 \(DE\)是允许调试特定的运行时体系结构的元素。  通常只有每个运行时环境的一 DE implementation。  
  
> [!NOTE]
>  当具有 Transact\-SQL 和 JScript 的单独 DE implementations， VBScript 和 JScript 共享单个 DE。  
  
 DE 与解释器或操作系统使用提供此调试服务与执行控制、断点和表达式计算。  这些服务通过 DE interfaces 实现，并可能导致调试器附加到差异操作状态之间的转换。  有关更多信息，请参见 [运行模式](../../extensibility/debugger/operational-modes.md)。  
  
 创建 DE 包括以下步骤:  
  
1.  注册 Visual Studio 的 DE  
  
2.  使程序进行调试  
  
3.  执行控制和状态计算  
  
4.  发送事件  
  
5.  停止和分离  
  
## 本节内容  
 [注册自定义调试引擎](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 解释步骤必要的注册了 Visual Studio 的调试引擎，以便可以使用它。  
  
 [启用要进行调试的程序](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 解释，在 DE 能调试过程之前，必须首先生成、或附加到现有程序。  
  
 [执行控制和状态评估](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 讨论调试应用程序的原因需要实现执行控制功能。  
  
 [发送事件](../../extensibility/debugger/sending-events.md)  
 描述调试器和 DE 之间的通信作为基于 DCOM 的事件模型。  
  
 [终止和分离](../../extensibility/debugger/termination-and-detaching.md)  
 解释如何实现正常终止，这意味着，没有断点、异常、运行时错误或无限循环访问应用程序进行调试。  
  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)  
 文档会在调试会话中的事件的调用序列。  
  
 [如何: 调试自定义调试引擎](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 解释如何调试自定义 DE。  
  
## 请参阅  
 [Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)