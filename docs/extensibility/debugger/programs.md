---
title: "程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e34dbcf9c19b5e8e7a16d2f409159597670cb8cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="programs"></a>Programs
在调试器体系结构，方面**程序**:  
  
-   是一套线程和的一组模块的容器。 在 Windows 操作系统的系统情况下，程序将具有任何单个的类比。  
  
     程序是一种类型的子进程。 例如，调试网站时，脚本可以视为程序。 虽然在脚本引擎进程中运行脚本，独立于其他脚本，它也具有其自己的一组线程。 调试引擎 (DE) 将附加到的程序，而不适用于进程或线程。  
  
-   可以识别本身以及它正在运行，并可以将其附加到另一个地址，分离，描述创建它，如果任何 DE 的过程。 程序可以执行、 停止、 继续，并终止。  
  
-   可以枚举所有线程。 程序也可以提供其自己的反汇编流，并可以枚举给定的文档位置的所有代码上下文。  
  
-   由[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)接口，创建附加程序之前，或作为附加的进程，具体取决于实现的一部分。 当一个端口枚举进程的程序时，根据相应创建每个程序[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)接口传递的自变量作为[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。 时的调试引擎还创建`IDebugProgram2`接口来表示程序，这些程序不会创建根据程序节点。 `IDebugProgramNode2`接口由 DE 用于实际调试时通过端口创建的那些仅用于发现哪些程序正在进程中运行。  
  
## <a name="see-also"></a>另请参阅  
 [进程](../../extensibility/debugger/processes.md)   
 [程序节点](../../extensibility/debugger/program-nodes.md)   
 [模块](../../extensibility/debugger/modules.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [调试引擎](../../extensibility/debugger/debug-engine.md)   
 [文档位置](../../extensibility/debugger/document-position.md)   
 [代码上下文](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)