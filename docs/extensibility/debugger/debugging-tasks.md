---
title: "调试任务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8bd22d71753a8bf86adbe2b437407481388c48d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-tasks"></a>调试任务
若要调试程序，它必须启动和调试引擎 (DE) 必须附加到它，否则 DE 必须连接到以前启动程序。 一旦附加，DE 必须生成某些启动事件。 在响应中，尝试绑定在 IDE 中设置断点调试包。 当程序达到绑定的断点时，它会中止并等待用户输入。  
  
## <a name="in-this-section"></a>本节内容  
 [安全问题](../../extensibility/debugger/security-issues.md)  
 讨论调试的程序所需的安全步骤。  
  
 [启动程序](../../extensibility/debugger/launching-a-program.md)  
 有关如何指定 DE，后者将调用以启动程序的操作系统提供分步说明。  
  
 [直接附加到程序](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 描述用于调试的程序已在运行的过程中的过程。  
  
 [启动后发送启动事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 列出 DE 附加到该程序，直到该程序位于其主入口点，并可供调试后发生的事件。  
  
 [控制执行](../../extensibility/debugger/control-of-execution.md)  
 说明如何 DE 通常情况下发送入口点事件、 负载完成的事件或 stopping 事件，具体取决于该情况。  
  
 [绑定断点](../../extensibility/debugger/binding-breakpoints.md)  
 介绍如何操作，如果用户设置断点，则 IDE 将依照请求并提示调试会话才能创建断点。  
  
 [计算表达式](../../extensibility/debugger/evaluating-expressions.md)  
 说明如何创建表达式和表达式进行求值时，会发生什么情况。  
  
 [可视化和查看数据](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 介绍表达式计算器 (EE) 如何支持类型可视化工具和自定义查看器。  
  
## <a name="related-sections"></a>相关章节  
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)  
 描述调试的主要体系结构概念。  
  
 [调试器组件](../../extensibility/debugger/debugger-components.md)  
 概述 Visual Studio 调试组件，包括 DE、 EE 和符号处理程序 (SH)。  
  
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)  
 说明 DE 如何同时运行代码、 文档和表达式评估上下文中。 描述，为每个三个上下文、 位置、 位置或评估与它相关。  
  
## <a name="see-also"></a>另请参阅  
 [入门](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)