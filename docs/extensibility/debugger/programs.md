---
title: "程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 12
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
ms.openlocfilehash: 982d966208433905115e76a36d358c656005e3d3
ms.lasthandoff: 02/22/2017

---
# <a name="programs"></a>Programs
在调试器体系结构，方面**程序**:  
  
-   是一组线程和一组模块的容器。 程序在 Windows 操作系统中有任何单个的类比。  
  
     程序是一种类型的子进程。 例如，调试 Web 站点时，脚本可以被视为程序。 虽然在脚本引擎进程中运行一个脚本，独立于其他脚本，它也具有其自己的一组线程。 调试引擎 (DE) 将附加到程序中，而不适用于进程或线程。  
  
-   可以识别本身以及它正在运行，并可以附加到另一个地址，分离，描述创建它，如果有的话 DE 的过程。 程序可以执行、 停止、 继续和终止。  
  
-   可以枚举其所有线程。 程序还可以提供其自己的反汇编流，并可以枚举给定的文档位置的所有代码上下文。  
  
-   由表示[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)创建附加程序之前，或作为连接过程，具体取决于实现的一部分的接口。 当一个端口枚举流程的程序时，根据相应创建每个程序[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)接口参数传递给[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。 虽然的调试引擎还创建`IDebugProgram2`接口来表示程序，这些程序不会创建根据程序节点。 `IDebugProgramNode2` DE 所创建的接口用于实际调试，而那些通过一个端口创建仅用于发现的进程中正在运行的程序。  
  
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
