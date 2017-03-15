---
title: "如何：在工作流中设置断点（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "断点, 在工作流中设置"
  - "调试工作流, 设置断点"
  - "调试, 在工作流中设置断点"
  - "工作流, 设置断点"
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 如何：在工作流中设置断点（旧版）
本主题介绍如何在使用旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 生成的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序中设置断点。在 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 应用程序需要面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 时，请使用旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 当使用 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中的旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 生成 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] 应用程序时，可像在 Visual Studio 中那样，在 C\# 和Visual Basic 代码中设置断点。正如预期的那样，工作流执行将在设置的每个断点处停止。  
  
 断点具有三个状态：“挂起”、“绑定”和“错误”。当您设置断点时，断点处于“挂起”状态，并且由一个空心的红色图标表示。当运行时加载了工作流类型后，断点将变为“绑定”状态，并且由一个实心的红色图标表示。如果为断点指定了不正确的格式，如同无效活动名称的情况一样，将出现一个错误窗口。断点仍然会添加到断点窗口，但标有一个小“x”。  
  
 可通过以下方式在工作流设计图面上设置活动断点：  
  
-   右击活动并选择**“断点”\\“插入断点”**。  
  
-   选择活动并按 F9。  
  
-   从**“调试”**菜单中选择**“新建断点”**。  
  
     您也可以使用此选项在调试时设置新断点，这时调试器将在断点处停止。  
  
    > [!NOTE]
    >  不支持在调用的工作流上设置断点。  
  
### 使用“调试”菜单上的“新建断点”选项设置断点  
  
1.  在**“调试”**菜单上，选择**“新建断点”**。  
  
2.  单击**“在函数处中断”**。  
  
     **“新建断点”**对话框将打开。  
  
3.  使用以下语法在**“函数”**文本框中指定活动的名称：`QualifiedActivityId[:[FullClassName][:InstanceId]]`。  
  
    > [!NOTE]
    >  （可选），您可以通过指定工作流活动的绝对路径来设置断点，而不是使用**“函数”**文本框中的活动名称。例如，假设有一个名为 **WorkflowConsoleApplication1** 的工作流解决方案，并且在该解决方案中有一个名为 **Workflow1** 的工作流，该工作流使用名为 **Delay1** 的活动。您可以使用活动名称 **Delay1**，或将路径指定为 **Delay1:WorkflowConsoleApplication1.Workflow1** 或 **Delay1:WorkflowConsoleApplication1.Workflow1:{6614886A\-608E\-412B\-BF98\-99FF1559DDDF}**。  
  
4.  选中**“使用 IntelliSense”**复选框以验证函数名称。  
  
     如果未选中此复选框，则不会执行断点名称验证。  
  
5.  从**“语言”**列表中选择**“工作流”**。  
  
6.  单击**“确定”**。  
  
## 请参阅  
 [调试旧版工作流](../workflow-designer/debugging-legacy-workflows.md)   
 [调用 Visual Studio Debugger for Windows Workflow Foundation（旧版）](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)