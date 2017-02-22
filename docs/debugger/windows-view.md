---
title: "Windows View | Microsoft Docs"
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
  - "vs.externaltools.spyplus.windowsview"
helpviewer_keywords: 
  - "Windows view"
ms.assetid: 154786ce-c803-4bfb-8198-f7962a900363
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Windows View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

首次打开 Spy\+\+ 时，窗口视图将显示包含系统中所有窗口和控件的树。  其中显示窗口句柄和类名称。  当前桌面窗口位于树的顶部。  所有其他窗口都是桌面的子窗口，并根据标准窗口层次结构列出。  同级窗口显示在其父窗口下方缩进的可扩展列表中。  
  
 下图显示顶级节点已扩展的典型 Spy\+\+ 窗口视图。  
  
 ![Spy&#43;&#43; 窗口视图](../debugger/media/spy--_windowsview.png "Spy\+\+\_WindowsView")  
Spy\+\+ 窗口视图  
  
 当前桌面窗口位于树的顶部。  所有其他窗口都是桌面的子窗口，并根据标准窗口层次结构列出，同级窗口按照 Z 顺序进行排序。  通过单击节点旁边的 \+ 或 \- 符号，您可以展开或折叠树的任何父节点。  
  
 如果“窗口”视图具有焦点，您可以使用[“窗口搜索”对话框](../debugger/window-search-dialog-box.md)中的“查找程序工具”显示系统中打开的任何窗口中的信息。  
  
## 本节内容  
 [How to: Use the Finder Tool](../Topic/How%20to:%20Use%20the%20Finder%20Tool.md)  
 显示此工具如何扫描窗口以查找属性或消息。  
  
 [How to: Search for a Window in Windows View](../debugger/how-to-search-for-a-window-in-windows-view.md)  
 说明如何在窗口视图中查找特定窗口。  
  
 [How to: Display Window Properties](../debugger/how-to-display-window-properties.md)  
 介绍打开“窗口属性”对话框的过程。  
  
## 相关章节  
 [Spy\+\+ Views](../debugger/spy-increment-views.md)  
 说明窗口、消息、进程和线程的 Spy\+\+ 树视图。  
  
 [Using Spy\+\+](../debugger/using-spy-increment.md)  
 介绍 Spy\+\+ 工具并说明如何使用。  
  
 [“查找窗口”对话框](../debugger/find-window-dialog-box.md)  
 用于查看特定窗口中的属性或消息。  
  
 [“窗口搜索”对话框](../debugger/window-search-dialog-box.md)  
 用于在窗口视图中查找特定窗口的节点。  
  
 [“窗口属性”对话框](../debugger/window-properties-dialog-box.md)  
 用于显示在窗口视图中选择的窗口的属性。  
  
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)  
 包含描述各个 Spy\+\+ 菜单和对话框的章节。