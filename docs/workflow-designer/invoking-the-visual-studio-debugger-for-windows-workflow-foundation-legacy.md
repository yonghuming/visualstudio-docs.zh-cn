---
title: "调用 Visual Studio Debugger for Windows Workflow Foundation （旧版） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: f56c7926e949511d90af20ce6789fe662c08e1c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>调用 Visual Studio Debugger for Windows Workflow Foundation（旧版）
本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试器在旧 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 中调试 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 应用程序。 在需要面向 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 时，请使用旧 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。  
  
 通常，您可以像调试用其他 Visual Studio 编程语言编写的程序那样来调试旧工作流。 您可以通过以下方式启动 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation：  
  
-   选择**附加到进程**上**调试**菜单从可用的进程选择正在运行的工作流实例。  
  
-   按**F5**来启动运行实例的工作流，或继续运行后命中断点。  
  
## <a name="stepping-through-code"></a>逐句通过代码  
 此调试器支持一个最常见的调试过程，即单步执行，此过程每次执行一行代码。 存在以下三个逐句通过代码的命令：  
  
-   **单步执行**： 可以单步执行活动使用**F11**。 此调试器可以单步执行任何定义的处理程序。 如果未定义处理程序，则可以逐过程执行该活动，或者对于包含其他活动的复合活动，您可以单步执行第一个要执行的活动。 单步执行代码处理程序从设计器不支持以下活动： **IfElseActivity**， **WhileActivity**， **ConditionedActivityGroup**，或**ReplicatorActivity**。 若要调试与这些活动关联的处理程序，你必须在代码中放置显式断点。  
  
-   **单步跳出**： 跳出活动使用**shift-f11**。 如果跳出某个活动，则会运行当前活动及其所有同级活动，直到这些活动完成为止。 然后调试器将在当前活动的父项处中断。 从代码处理程序中跳出时，调试器将在与此处理程序关联的活动处中断。  
  
-   **逐过程**： 你可以逐过程执行活动使用**F10**。 逐过程执行复合活动时， 调试器将在此复合活动的第一个可执行的子活动处中断。 逐过程进行非复合，如**CodeActivity**活动，调试器将执行活动及其关联的处理程序和分页符上的下一个活动。 如果执行的活动是复合活动中的最后一个子活动，则在执行之后，调试器将在父活动处中断。  
  
## <a name="attaching-to-a-process"></a>附加到进程  
 若要通过附加到进程中调试工作流，选择可用进程从**可用进程**列表框中的**附加到进程**对话框。 如果**自动： 工作流代码**才会显示在**将附加到**文本，然后单击**选择**。 在**选择代码类型**对话框中，单击**调试以下代码类型**和选择**工作流**。 然后单击**确定**单击**附加**。  
  
## <a name="debugging-with-f5"></a>用 F5 调试  
 如果工作流主机应用程序和工作流 DLL 位于不同的 Visual Studio 项目，例如，当你使用工作流活动库时，你必须将工作流 DLL 项目设置为 Visual Studio 解决方案启动项目，以便调试工作流使用**F5**。 你还必须设置的路径中的工作流 DLL 项目的主机应用程序**启动外部程序**属性。  
  
 在解决方案资源管理器中设置启动项目，右键单击项目名称，然后选择**设为启动项目**。 将路径设置到中的主机**启动外部程序**属性，双击工作流项目的**属性**在解决方案资源管理器，选择的节点**调试**选项卡。下**启动操作**，选择**启动外部程序**并输入承载要调试的工作流的.exe 文件的路径。  
  
 如果将主机应用程序设置为启动项目，则只调用 Visual Studio 调试器来进行调试；不会调用 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation。 如果使用 Visual Studio 调试器，则只会命中 C# 或 Visual Basic 代码断点；而不会命中在工作流设计器中设置的断点。 例如，如果使用 <xref:System.Workflow.Activities.ParallelActivity> Debugger for Windows Workflow Foundation，则会命中您在设计器中在 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 活动处设置的断点，如果使用 Visual Studio 调试器，则不会命中此断点。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 在工作流 （旧版） 中设置断点](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [调试旧版工作流](../workflow-designer/debugging-legacy-workflows.md)