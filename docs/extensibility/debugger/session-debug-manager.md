---
title: "会话调试管理器 | Microsoft Docs"
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
  - "会话调试管理器中，统一会话视图"
  - "会话调试管理器广播"
  - "调试 [调试 SDK]，会话调试管理器"
  - "会话调试管理器"
  - "会话调试管理器中，调试引擎进行多路复用"
  - "会话调试管理器中委托"
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 会话调试管理器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

会议任意数量的计算机进行管理任意数量的调试引擎 \(DE\)调试在多个管理器 \(SDM\)的任意数量的处理程序。  除了冗长之外调试引擎复用器， SDM 提供调试会话的一个统一的视图对 IDE。  
  
## 会话调试管理器操作  
 会议调试管理器 \(SDM\)管理 DE。  可以包含多个调试同时运行于设备的引擎。  若要进行多路复用 DES， SDM 换行从 DES 的接口并将它们显示在 IDE 作为单个接口中。  
  
 若要提高性能，某些接口未进行多路复用。  相反，它们直接从、使用，并调用这些接口不通过 SDM。  例如，在中，因为它们在特定 DE，调试的特定程序引用特定命令，内存或文档使用的接口与内存，代码，并文档上下文未进行多路复用。  其他 DE 在通信的该级别不需要参与。  
  
 这不是真正的所有上下文。  调用表达式计算上下文接口的 SDM。  在计算表达式时， SDM 包装为 IDE 的 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 接口，这是因为，如果该计算表达式时，它可能会位于相同的调试程序处理可能运行在同一线程上的多个 DES。  
  
 SDM 通常作为委托结构，但是，它可能作为广播机制。  例如，在计算表达式时， SDM 作为广播机制通知所有 DES 它们可以运行在指定的线程的代码。  同样，那么，当 SDM 接收的终止的事件时，广播给它们应停止运行的所有过程。  当步骤调用时， SDM 广播到他们可以继续运行的所有过程。  断点也广播到每个 DE。  
  
 SDM 不跟踪当前程序、线程或堆栈帧。  处理、过程和线程信息发送到 SDM 与特定调试事件结合使用。  
  
## 请参阅  
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [调试程序组件](../../extensibility/debugger/debugger-components.md)   
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)