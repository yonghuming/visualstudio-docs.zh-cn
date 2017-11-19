---
title: "启动程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29e05c7cef8b7bc8644ccbf7ea542e2f043547a6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="launching-a-program"></a>启动程序
想要调试的程序的用户可以按 f5 键以从 IDE 运行调试器。 该解决方案从开始一系列事件，最终导致 IDE 的连接到调试引擎 (DE)，后者反过来连接，或附加，到程序，如下所示：  
  
1.  IDE 首先调用项目包可以获取调试设置的解决方案的活动项目。 设置包括的开始目录、 环境变量，该程序将在其中运行的端口和 DE 要用于创建程序，如果指定。 这些设置将传递到调试包。  
  
2.  如果指定 DE，DE 调用操作系统启动程序。 正在启动程序，因此加载程序的运行时环境。 例如，如果程序在 MSIL 中编写的公共语言运行时将调用以运行程序。  
  
     - 或 -  
  
     如果未指定 DE，端口调用操作系统启动程序，这会导致要加载的程序的运行时环境。  
  
    > [!NOTE]
    >  如果 DE 用于启动的某个程序，则很可能相同 DE 将被附加到该程序。  
  
3.  具体取决于是否 DE 或端口启动程序，DE 或运行时环境的程序说明或节点，然后创建通知运行程序的端口。  
  
    > [!NOTE]
    >  建议的运行时环境创建程序节点中，因为该程序节点是可以调试程序的轻量表示。 没有无需加载整个 DE 只是为了创建和注册程序节点。 如果设计 DE IDE 中，但没有 IDE 的进程中运行为实际上正在运行，需要有一个组件，可以将程序节点添加到的端口。  
  
 新创建的程序，以及任何其他程序，相关或不相关的、 启动或附加到相同的 IDE 中，从撰写调试会话。  
  
 以编程方式，当用户第一次按**F5**，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的调试包调用项目包 （这与启动的程序的类型是关联） 通过<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>方法，反过来填写<xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2>结构解决方案的活动项目调试设置。 此结构传递回调试包上，通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A>方法。 调试包然后实例化启动正在调试和任何关联的调试引擎的程序的会话调试管理器 (SDM)。  
  
 传递给 SDM 的自变量之一是 DE 要用于启动程序的 GUID。  
  
 如果 DE GUID 不是`GUID_NULL`，SDM 共同创建 DE，，然后调用其[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法来启动程序。 例如，如果程序用本机代码，然后编写`IDebugEngineLaunch2::LaunchSuspended`将可能调用`CreateProcess`和`ResumeThread`（Win32 函数），以运行该程序。  
  
 正在启动程序，因此加载程序的运行时环境。 然后创建 DE 或运行时环境[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)接口来描述该程序，并将传递到此接口[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)通知的程序的端口运行。  
  
 如果`GUID_NULL`传递，则端口启动的程序。 程序开始运行后，运行时环境创建`IDebugProgramNode2`接口来描述该程序，并将其传递给`IDebugPortNotify2::AddProgramNode`。 这将通知运行程序的端口。 然后 SDM 将附加到正在运行的程序的调试引擎。  
  
## <a name="in-this-section"></a>本节内容  
 [通知端口](../../extensibility/debugger/notifying-the-port.md)  
 说明将启动一个程序，并通知端口后，会发生什么情况。  
  
 [启动后附加](../../extensibility/debugger/attaching-after-a-launch.md)  
 在调试会话已准备好将 DE 附加到程序时的文档。  
  
## <a name="related-sections"></a>相关章节  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)  
 包含指向不同的调试任务，如启动程序和计算表达式。