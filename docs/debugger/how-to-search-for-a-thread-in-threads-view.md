---
title: "How to: Search for a Thread in Threads View | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threads, searching"
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Search for a Thread in Threads View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用线程 ID 或模块字符串作为搜索条件，从而在线程视图中搜索特定线程。  此外，还可以指定搜索的初始方向。  对话框中的字段将显示线程树中所选线程的特性。  
  
### 在线程视图中搜索线程  
  
1.  排列窗口，以便 Spy\+\+ 和活动[线程视图](../debugger/threads-view.md)窗口可见。  
  
2.  从“搜索”菜单中选择“查找线程”。  
  
     [“线程搜索”对话框](../debugger/thread-search-dialog-box.md)随即打开。  
  
3.  键入线程 ID 或模块字符串作为搜索条件。  
  
4.  清除不想为其指定值的任何字段。  
  
    > [!TIP]
    >  若要查找模块拥有的所有线程，请清除“线程”文本框，并在“模块”框中键入模块名称。  然后使用“查找下一个”继续搜索线程。  
  
5.  对于搜索的初始方向，选择“向上”或“向下”。  
  
6.  单击**“确定”**。  
  
 如果找到匹配的线程，将在线程视图窗口中突出显示该线程。