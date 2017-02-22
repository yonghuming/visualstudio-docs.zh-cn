---
title: "调用 Visual Studio Debugger for Windows Workflow Foundation（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "调试器, 工作流"
  - "调试工作流, 启动调试器"
  - "调试, 使用工作流调试器"
  - "“单步执行”命令"
  - "“跳出”命令"
  - "“逐过程”命令"
  - "单步执行"
  - "单步执行, 命令"
  - "工作流调试器, 开始"
  - "工作流, 调试器"
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 调用 Visual Studio Debugger for Windows Workflow Foundation（旧版）
本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试器在旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中调试 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序。在需要面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 时，请使用旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 通常，您可以像调试用其他 Visual Studio 编程语言编写的程序那样来调试旧工作流。您可以通过以下方式启动 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation：  
  
-   选择**“调试”**菜单上的**“附加到进程”**以从可用进程中选择正在运行的工作流实例。  
  
-   按 **F5** 以开始运行工作流实例，或者在命中断点后继续运行。  
  
## 逐句通过代码  
 此调试器支持一个最常见的调试过程，即单步执行，此过程每次执行一行代码。存在以下三个逐句通过代码的命令：  
  
-   **单步执行**：可以使用 **F11** 来单步执行某个活动。此调试器可以单步执行任何定义的处理程序。如果未定义处理程序，则可以逐过程执行该活动，或者对于包含其他活动的复合活动，您可以单步执行第一个要执行的活动。对于以下活动，不支持从设计器中单步执行代码处理程序：**IfElseActivity**、**WhileActivity**、**ConditionedActivityGroup** 或 **ReplicatorActivity**。若要调试与这些活动关联的处理程序，您必须在代码中放置显式断点。  
  
-   **跳出**：您可以使用 **Shift\-F11** 跳出某个活动。如果跳出某个活动，则会运行当前活动及其所有同级活动，直到这些活动完成为止。然后调试器将在当前活动的父项处中断。从代码处理程序中跳出时，调试器将在与此处理程序关联的活动处中断。  
  
-   **逐过程**：您可以使用 **F10** 逐过程执行某个活动。当逐复合的活动。调试器将在此复合活动的第一个可执行的子活动处中断。逐过程执行非复合活动时，例如 **CodeActivity** 活动，调试器将执行此活动及其关联的处理程序并在下一个活动处中断。如果执行的活动是复合活动中的最后一个子活动，则在执行之后，调试器将在父活动处中断。  
  
## 附加到进程  
 若要通过附加到进程来调试工作流，请从**“附加到进程”**对话框内的**“可用进程”**列表框中选择可用进程。如果**“自动:工作流代码”**未显示在**“附加到”**文本框中，则单击**“选择”**。在**“选择代码类型”**对话框中单击**“调试以下代码类型”**，再选择**“工作流”**。然后单击**“确定”**，并单击**“附加”**。  
  
## 用 F5 调试  
 如果工作流主机应用程序和工作流 DLL 位于不同的 Visual Studio 项目中，例如，在使用工作流 Activity 库时，则必须将工作流 DLL 项目设置为 Visual Studio 解决方案启动项目，以便使用 **F5** 调试工作流。还必须在工作流 DLL 项目的**“启动外部程序”**属性中设置主机应用程序的路径。  
  
 若要在解决方案资源管理器中设置启动项目，请右击项目名称，并选择**“设为启动项目”**。若要在**“启动外部程序”**属性中设置宿主的路径，请在解决方案资源管理器中双击工作流项目的**“属性”**节点，并选择**“调试”**选项卡。在**“启动操作”**下面选择**“启动外部程序”**，并输入承载要调试的工作流的 .exe 文件的路径。  
  
 如果将主机应用程序设置为启动项目，则只调用 Visual Studio 调试器来进行调试；不会调用 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation。如果使用 Visual Studio 调试器，则只会命中 C\# 或 Visual Basic 代码断点；而不会命中在工作流设计器中设置的断点。例如，如果使用 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation，则会命中您在设计器中在 <xref:System.Workflow.Activities.ParallelActivity> 活动处设置的断点，如果使用 Visual Studio 调试器，则不会命中此断点。  
  
## 请参阅  
 [如何：在工作流中设置断点（旧版）](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [调试旧版工作流](../workflow-designer/debugging-legacy-workflows.md)