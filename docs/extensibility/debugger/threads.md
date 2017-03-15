---
title: "线程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6faced71ba03bcf1c4bf1849515bdf7b4fe455f8
ms.lasthandoff: 02/22/2017

---
# <a name="threads"></a>线程
在调试器体系结构，方面**线程**:  
  
-   是计算的基本单元。 线程按顺序执行它的上下文中的单一调用堆栈，将从一种代码上下文移到下一步的说明。  
  
-   可以识别本身以及它正在运行，并且可以是名为、 挂起，并恢复该程序。 线程还可以枚举其关联的堆栈帧，而且在某些情况下可以移到另一个堆栈帧。 给定堆栈帧上下文内的，一个线程可以返回其关联的逻辑线程，如果有的话。 线程都具有属性，如挂起计数，可以显示在 IDE 的线程窗口中。  
  
-   由表示[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)通常的调试引擎 (DE) 或虚拟机，因此执行程序创建的接口。  
  
## <a name="see-also"></a>另请参阅  
 [程序](../../extensibility/debugger/programs.md)   
 [堆栈帧](../../extensibility/debugger/stack-frames.md)   
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [会话调试管理器](../../extensibility/debugger/session-debug-manager.md)
