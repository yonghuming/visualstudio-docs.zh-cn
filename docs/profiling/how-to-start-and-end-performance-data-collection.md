---
title: "如何：启动和结束分析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.wizard.summarypage"
helpviewer_keywords: 
  - "分析工具, 启动会话"
  - "性能会话, 启动"
  - "性能会话, 结束"
  - "分析工具, 结束会话"
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：启动和结束分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

启动分析之前，必须将要分析的目标二进制文件添加到性能会话中。  若要添加目标，请在**“性能资源管理器”**中右击**“目标”**，然后单击**“添加目标二进制文件”**。  在**“添加目标二进制文件”**对话框中，选择文件名，然后单击**“打开”**。  将添加一个新的二进制文件。  
  
### 启动分析  
  
1.  在**“性能资源管理器”**窗口上右击性能会话的名称，然后选择以下选项之一：  
  
    -   **启动并启用分析功能** \- 启动应用程序并立即开始分析。  
  
    -   **启动并暂停分析** \- 启动应用程序，但不开始分析。  可以通过在**“数据收集控件”**窗口中选择**“继续收集”**来启动分析。  有关更多信息，请参见[如何：暂停和继续分析](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md)。  
  
### 结束分析  
  
-   结束分析会话的首选方法是退出应用程序。  若要立即停止分析，请在**“性能资源管理器”**工具栏上单击**“停止”**。  
  
## 请参阅  
 [控制数据收集](../profiling/controlling-data-collection.md)   
 [如何：暂停和继续分析](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md)