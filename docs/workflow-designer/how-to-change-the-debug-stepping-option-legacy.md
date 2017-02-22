---
title: "如何：更改调试单步执行选项（旧版） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "分支单步执行"
  - "调试工作流, 单步执行选项"
  - "调试, 单步执行选项"
  - "实例单步执行"
  - "单步执行, 更改选项"
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 如何：更改调试单步执行选项（旧版）
本主题介绍如何在旧 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中，针对具有并发操作的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 应用程序更改调试单步执行选项。在需要面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 时，请使用旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。  
  
 在调试具有并发执行的旧活动（例如，**ParallelActivity** 或 **ConditionedActivityGroup**）时，可以使用两个选项之一来逐句通过代码。  
  
 按照这些步骤在旧工作流项目中更改调试单步执行选项。  
  
## 过程  
  
#### 更改调试单步执行选项  
  
1.  启动 Visual Studio。  
  
2.  打开现有的旧工作流项目，或创建使用并发活动并且面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 的新项目。  
  
3.  在旧 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的**“工作流”**菜单上，指向 **“调试”**，然后指向**“单步执行选项”**。  
  
4.  选择**“实例”**或**“分支”**。  
  
## 请参阅  
 [调试旧版工作流](../workflow-designer/debugging-legacy-workflows.md)   
 [调试单步执行选项（旧版）](../workflow-designer/debug-stepping-options-legacy.md)