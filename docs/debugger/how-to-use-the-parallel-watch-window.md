---
title: "如何：使用“并行监视”窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.parallelwatch"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试器, 并行监视窗口"
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用“并行监视”窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在“并行监视”窗口中，您可同时显示一个表达式保留在多个线程上的值。  每个行均表示一个在应用程序中运行的线程，但一个线程可能用多个行表示。  更具体地说，每个行均表示一个函数调用，其函数签名与当前堆栈帧上的函数的签名匹配。  您可以对列中的项进行排序、重新排序、移除和分组操作。  您可标记、取消标记、冻结（禁止显示）和解冻（恢复）线程。  下面的列将显示在**“并行监视”**窗口中：  
  
-   标记列，可在其中标记要特别注意的线程。  
  
-   帧列，其中箭头指示选定的帧。  
  
-   可配置的列，可显示计算机、进程、平铺、任务和线程。  
  
    > [!TIP]
    >  您必须打开**“并行任务”**窗口以便在**“并行监视”**窗口中显示任务信息。  
  
-   **“\<添加监视\>”**列，可在其中输入要监视的表达式。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 显示“并行监视”窗口  
  
1.  在代码中设置断点。  
  
2.  在菜单栏上，依次选择**“调试”**、**“启动调试”**。  等待应用程序到达断点。  
  
3.  在菜单栏上，依次选择**“调试”**、**“窗口”**、**“并行监视”**和监视窗口。  您可打开最多 4 个窗口。  
  
### 添加监视表达式  
  
-   选择**“\<添加监视\>”**，然后指定监视表达式。  
  
### 标记或取消标记线程  
  
-   选择行的标记列，或打开线程的快捷菜单并选择**“标记”**或**“取消标记”**。  
  
### 仅显示标记的线程  
  
-   选择**“并行监视”**窗口左上角的“仅显示标记的线程”按钮。  
  
### 切换帧  
  
-   双击帧列。（键盘：选择行，然后按 Enter。）  
  
### 为列排序  
  
-   选择列标题。  
  
### 分组线程  
  
-   打开“并行监视”窗口的快捷菜单，选择**“分组依据”**，然后选择相应的子菜单项。  
  
### 冻结或解冻线程  
  
-   打开行的快捷菜单，然后选择**“冻结”**或**“解冻”**。  
  
### 导出“并行监视”窗口中的数据  
  
-   选择**“在 Excel 中打开”**按钮，然后选择**“在 Excel 中打开”**或**“导出到 CSV”**。  
  
### 按布尔表达式筛选  
  
-   在**“按布尔表达式筛选”**框中输入一个布尔表达式。  调试器将为每个线程上下文计算此表达式。  仅显示其中的值为 `true` 的行。  
  
## 请参阅  
 [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：使用“GPU 线程”窗口](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)   
 [演练：调试 C\+\+ AMP 应用程序](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)