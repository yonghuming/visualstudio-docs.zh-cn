---
title: "创建自定义调试引擎 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb5971bf86c6b97d38daaf86f3a093da196020da
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-custom-debug-engine"></a>创建自定义调试引擎
调试引擎 (DE) 是允许对特定运行时体系结构进行调试的组件。 通常是每个运行时环境的只有一个 DE 实现。  
  
> [!NOTE]
>  虽然有 TRANSACT-SQL 的单独 DE 实现并且 JScript、 VBScript 和 JScript 共享单个 DE。  
  
 DE 适用于解释器或操作系统提供执行控件、 断点及表达式评估等调试服务。 这些服务通过 DE 接口实现，并可能导致不同的运行模式之间的转换到调试器。 有关详细信息，请参阅[运行模式](../../extensibility/debugger/operational-modes.md)。  
  
 创建 DE 包含以下步骤：  
  
1.  使用 Visual Studio 注册 DE  
  
2.  启用要调试程序  
  
3.  执行控制和状态评估  
  
4.  发送事件  
  
5.  终止和分离  
  
## <a name="in-this-section"></a>本节内容  
 [注册自定义调试引擎](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 说明注册随 Visual Studio 的调试引擎，以便可以使用它所需的步骤。  
  
 [启用要进行调试的程序](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 说明你 DE 可以调试的程序之前，您必须首先启动 DE 或将其附加到的现有程序。  
  
 [执行控件和状态计算](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 讨论为什么调试应用程序需要实现执行控件功能。  
  
 [发送事件](../../extensibility/debugger/sending-events.md)  
 介绍了作为基于 DCOM 的事件模型调试器和 DE 之间的通信。  
  
 [终止和分离](../../extensibility/debugger/termination-and-detaching.md)  
 说明如何实现正常终止，这意味着没有断点、 异常、 运行时错误或在应用程序要调试的无限循环。  
  
 [调用调试器事件](../../extensibility/debugger/calling-debugger-events.md)  
 记录在调试会话中发生的事件的调用顺序。  
  
 [如何：调试自定义调试引擎](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 说明如何调试自定义 DE。  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)