---
title: "调试任务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 16
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
ms.openlocfilehash: 08f6d64a86982ad7425a2e89815765ce63dbf28c
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-tasks"></a>调试任务
若要调试程序，则必须启动该程序，调试引擎 (DE) 必须附加到它，或者 DE 必须附加到先前启动的程序。 一旦附加，DE 必须生成某些启动事件。 在响应中，尝试绑定在 IDE 中设置断点调试包。 当程序达到绑定的断点时，它将暂停并等待用户输入。  
  
## <a name="in-this-section"></a>本节内容  
 [安全问题](../../extensibility/debugger/security-issues.md)  
 讨论调试程序所需的安全步骤。  
  
 [下启动程序](../../extensibility/debugger/launching-a-program.md)  
 提供有关如何指定 DE，后者调用操作系统来启动程序的分步说明。  
  
 [将直接连接到某个程序](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 描述用于调试的程序在已运行的进程的过程。  
  
 [发送应用程序启动后启动事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 列出 DE 附加到程序，直到该程序位于其主入口点，并可进行调试后发生的事件。  
  
 [控制执行](../../extensibility/debugger/control-of-execution.md)  
 说明如何 DE 通常情况下发送入口点事件、 负载完成的事件或停止事件，根据不同环境。  
  
 [绑定断点](../../extensibility/debugger/binding-breakpoints.md)  
 描述如何，如果用户设置一个断点，则 IDE 将形成请求和提示调试会话才能创建断点。  
  
 [计算表达式](../../extensibility/debugger/evaluating-expressions.md)  
 说明如何创建表达式和表达式进行求值时，会发生什么情况。  
  
 [可视化和查看数据](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 说明表达式计算器 (EE) 如何支持类型的可视化工具和自定义查看器。  
  
## <a name="related-sections"></a>相关章节  
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)  
 描述调试的主要体系结构概念。  
  
 [调试程序组件](../../extensibility/debugger/debugger-components.md)  
 提供 Visual Studio 调试组件，包括 DE、 EE 和符号处理程序 (SH) 的概述。  
  
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)  
 解释 DE 方式同时代码、 文档和表达式计算上下文中。 描述，每个算法的三个上下文、 位置、 位置或评估与它相关。  
  
## <a name="see-also"></a>另请参阅  
 [入门](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
