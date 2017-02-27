---
title: "如何：配置分析工具性能规则 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.ruleseditor"
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：配置分析工具性能规则
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio分析工具的性能警告指示被分析应用程序中存在可能减慢程序执行的问题。  警告还指示可能需要更改收集方法才能收集更多有用的数据。  在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中打开分析数据文件时，系统会在分析会话中自动生成性能警告，并会将这些警告显示在“错误列表”窗口中。  某些警告可能不适用于您所关注的情况，并且可能错误地引发某些警告。  可以配置性能警告以显示或隐藏特定警告。  
  
### 配置探查器性能警告  
  
1.  在**“工具”**菜单上，单击**“选项”**。  
  
2.  展开**“性能工具”**节点，然后单击**“规则”**。  
  
3.  若要启用或禁用某个警告，请选中或清除该警告的 **ID** 和名称旁边的复选框。  
  
4.  若要指定某条规则的警告等级，请单击该规则旁边的**“操作”**单元格，然后单击警告等级。  
  
    -   **“禁用”** \- 禁用该规则（其效果等同于清除规则 ID 旁边的复选框）。  
  
    -   **“警告”** \- 将该规则显示为警告。  
  
    -   **“错误”** \- 暂停分析执行并将该规则显示为错误。  
  
    -   **“信息”** \- 仅将该规则显示为信息性文字。