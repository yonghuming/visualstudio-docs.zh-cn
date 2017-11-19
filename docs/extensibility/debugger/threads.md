---
title: "线程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 150e27c4b8df06784848829bfe713773cf9d48a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="threads"></a>线程
在调试器体系结构，方面**线程**:  
  
-   是计算的基本单位。 线程按顺序执行它的上下文中的单个调用堆栈，将从一种代码上下文移至下一步的说明。  
  
-   可以识别本身以及它在中，运行可以和名为、 挂起，然后恢复该程序。 线程也可以枚举其关联的堆栈帧，并在某些情况下可以移到另一个堆栈帧。 给定堆栈帧的上下文，线程可以返回其关联的逻辑线程，如果有的话。 线程具有属性，如挂起计数，可以在 IDE 的线程窗口中显示。  
  
-   由[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)接口，通常创建的调试引擎 (DE) 或虚拟机，因此执行程序。  
  
## <a name="see-also"></a>另请参阅  
 [程序](../../extensibility/debugger/programs.md)   
 [堆栈帧](../../extensibility/debugger/stack-frames.md)   
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [会话调试管理器](../../extensibility/debugger/session-debug-manager.md)