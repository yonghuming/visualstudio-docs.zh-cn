---
title: "调试旧版工作流 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2253eb414e58d5168cf6e1d2f4c22880d18d1bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugging-legacy-workflows"></a>调试旧版工作流
如果要用 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中的传统 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 构建面向 .NET Framework 3.0 或 3.5 的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序，可以像对其他程序一样，通过设置断点、附加到进程、检查线程和调用堆栈来调试工作流。 您还可以选择远程调试。  
  
> [!NOTE]
>  如果计算机上安装并卸载过 Visual Studio 的多个版本，在以下两种情况下 WF3 调试可能失败：  
>   
>  -   设置的断点未命中。  
> -   显示以下消息：  
>   
>  **无法启动 web 服务器上进行调试。调试程序安装不正确。无法对请求的代码类型进行调试。运行安装程序以安装或修复调试器。**  
>   
>  如果在调试 .NET Framework 3.0 或 3.5 工作流时发生以上任一情况，请对 Visual Studio 安装进行修复。  
  
 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 集成具有以下标准 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试窗口：  
  
-   **断点**： 按预期工作，但你指定的函数名称的活动。  
  
-   **调用堆栈**： 已修改，以提供工作流实例中执行的活动的概述。 中的条目**调用堆栈**窗口是深度优先搜索得出的执行的活动。 您可以双击某个项以将焦点放在选定的活动上。  
  
-   **线程**： 提供正在调试的工作流实例的实例 ID。  
  
 Visual Studio for Windows Workflow Foundation 不支持以下调试功能：  
  
-   设计器图面上的条件断点。  
  
-   QuickWatch。  
  
-   设置下一语句。  
  
-   运行到光标处。  
  
-   编辑并继续。  
  
-   实时调试。  
  
-   混合模式调试。  
  
## <a name="in-this-section"></a>本节内容  
 [调用 Visual Studio Debugger for Windows Workflow Foundation（旧版）](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [禁用 Visual Studio Debugger for Windows Workflow Foundation（旧版）](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [如何：调试基于 ASP.NET 的工作流（旧版）](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [如何：在工作流中设置断点（旧版）](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [通过远程计算机调试工作流（旧版）](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [调试单步执行选项（旧版）](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [如何：更改调试单步执行选项（旧版）](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)