---
title: "程序节点 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6deae60a8e7863e19ec0624ff6452bf41816070
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="program-nodes"></a>程序节点
在调试器体系结构，方面**程序节点**:  
  
-   是程序的轻型描述。  
  
-   可以识别本身以及它正在运行，并将其附加到另一个地址，分离，描述创建它，如果任何的调试引擎 (DE) 的过程。  
  
-   由[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)接口，通常由 DE 或端口。 程序节点添加到端口通过调用[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。 当程序节点添加到某个端口后时，它被添加到包含此程序节点表示程序进程。  
  
 调试会话已启动过一段时间，具体取决于调试包中，实现后程序节点用于创建相应的程序。 在其程序查询进程，将枚举程序，一个用于每个程序节点。  
  
 程序附加到之前，IDE 将需要仅在程序的轻型说明。 可以从程序节点中获取此信息。 一旦程序附加到，IDE 将需要显示更多详细的信息，如在程序中运行的所有线程的列表。 从程序本身中获取此信息。  
  
## <a name="see-also"></a>另请参阅  
 [程序](../../extensibility/debugger/programs.md)   
 [进程](../../extensibility/debugger/processes.md)   
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)