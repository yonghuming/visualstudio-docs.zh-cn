---
title: "How to: Search for a Process in Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Processes view"
  - "processes, searching for"
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Process in Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用进程 ID 或模块字符串作为搜索条件，从而在进程视图中搜索特定进程。  此外，还可以指定搜索的初始方向。  对话框中的字段将显示进程树中所选进程的特性。  
  
### 在进程视图中搜索进程  
  
1.  排列窗口，以便 Spy\+\+ 和活动[进程视图](../debugger/processes-view.md)窗口可见。  
  
2.  从“搜索”菜单中选择“查找进程”  
  
     [“进程搜索”对话框](../debugger/process-search-dialog-box.md)随即打开。  
  
3.  键入进程 ID 或模块字符串作为搜索条件。  
  
4.  清除不想为其指定值的任何字段。  
  
    > [!TIP]
    >  若要查找模块拥有的所有进程，请清除“进程”框，然后在“模块”框中键入模块名称。  然后使用“查找下一个”继续搜索进程。  
  
5.  对于搜索的初始方向，选择“向上”或“向下”。  
  
6.  单击**“确定”**。  
  
 如果找到匹配的进程，将在“进程视图”窗口中突出显示该进程。