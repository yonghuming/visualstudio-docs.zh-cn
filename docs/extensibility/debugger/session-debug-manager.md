---
title: "会话调试 Manager |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8100c43578c11ae73f26764df74aa17caccc3611
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="session-debug-manager"></a>会话调试管理器
会话调试管理器 (SDM) 管理任意数量的调试引擎 (DE) 调试任意数量的任意数量的计算机上的多个进程中的程序。 除了多路复用器调试引擎外，SDM 到 IDE 提供调试会话的统一的视图。  
  
## <a name="session-debug-manager-operation"></a>会话调试管理器操作  
 会话调试管理器 (SDM) 管理 DE。 可能在同一时间的计算机上运行的多个调试引擎。 若要多路复用 DEs，SDM 包装大量从 DEs 接口，并将它们公开为作为单个接口 IDE。  
  
 为了提高性能，有些接口进行不多路复用。 相反，它们用于直接从 DE，并对这些接口的调用不会通过 SDM。 例如，使用与内存、 代码和文档上下文接口进行不多路复用，因为它们是指特定指令、 内存或在通过特定 DE 进行调试的特定程序的文档。 没有其他 DE 需要涉及在该级别的通信。  
  
 这不是 true 的所有上下文。 对表达式评估上下文接口调用经历 SDM。 在表达式计算过程 SDM 包装[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口，它使 IDE 因为时计算该表达式，它可能涉及到多个正在调试程序在同一进程中可能的 DEs在同一线程上运行。  
  
 SDM 通常充当一种委派机制，但它可能充当广播的机制。 例如，在表达式计算过程 SDM 充当广播的机制以通知所有的 DEs，它们可以在指定的线程上运行代码。 同样，当 SDM 收到 stopping 事件，它将广播到应停止运行的所有程序。 当调用一个步骤时，SDM 广播到所有程序，它们可以继续运行。 断点还会传播至每个 DE。  
  
 SDM 不跟踪当前程序、 线程或堆栈帧。 过程、 程序和线程信息发送到与特定的调试事件一起 SDM。  
  
## <a name="see-also"></a>另请参阅  
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [调试器组件](../../extensibility/debugger/debugger-components.md)   
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)