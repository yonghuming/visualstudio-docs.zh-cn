---
title: "如何：比较探查器数据文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.choosediffbinaries"
helpviewer_keywords: 
  - "探查器结果文件, 如何比较"
  - "分析工具, 如何比较探查器结果文件"
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# 如何：比较探查器数据文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以通过创建比较（“Diff”）报告或视图来比较两个不同的探查器数据文件（.vsp 或 .vsps）的结果。  通过比较可以了解一个分析会话与另一个分析会话的不同、性能衰退以及改进。  
  
 Diff 报告的数据以表的形式显示。  该表显示与基线相比后的增量或变化。  这是通过确定旧值、基线值和新分析的结果值之间的差异计算而来的。  
  
 探查器数据的比较基于代码中的函数、应用程序中的模块、行、指令指针 \(IP\) 和类型。  
  
 可以设置一个阈值来降噪，并筛选出未按指定量更改的行的表视图中的所有数据。  
  
### 为性能资源管理器中的项目创建比较文件视图  
  
1.  在**“性能资源管理器”**的**“报告”**下，选择要用作比较基线值的 .vsp 或 .vsps 报告文件。  
  
2.  选择要比较的 .vsp 或 .vsps 报告文件。  
  
3.  右击选定的文件之一，然后单击**“比较报告”**。  
  
### 比较值  
  
1.  在“报告视图”窗口中选择**“比较报告”**选项卡。  
  
2.  在**“表”**下拉列表中，选择要比较的函数或模块。  
  
3.  在**“列”**下拉列表中，选择要比较的值。  
  
4.  （可选）键入**“阈值”**的值。  
  
5.  单击**“应用”**。  
  
### 比较报告文件  
  
1.  在**“分析”**菜单上，选择**“比较性能报告”**。  
  
2.  在**“选择要比较的分析文件”**窗口中，浏览并选择**“基线文件”**分析文件（.vsp 或 .vsps）和**“比较文件”**（.vsp 或 .vsps）。  
  
3.  单击**“确定”**。