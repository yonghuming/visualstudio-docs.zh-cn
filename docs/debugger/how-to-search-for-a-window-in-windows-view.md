---
title: "How to: Search for a Window in Windows View | Microsoft Docs"
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
  - "windows, searching in Windows view"
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Search for a Window in Windows View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用窗口的句柄、标题、类或其标题和类的组合作为搜索条件，从而在窗口视图中搜索特定窗口。  此外，还可以指定搜索的初始方向。  对话框中的字段将显示窗口树中所选窗口的特性。  
  
 从扩展到第二层（所有窗口都是桌面的子窗口）的树开始，以便您可以按窗口的类名称和标题标识桌面级窗口。  选择桌面级窗口后，您可以展开该级别以查找特定子窗口。  
  
### 在窗口视图中搜索窗口  
  
1.  排列窗口，以便 Spy\+\+、[窗口视图](../debugger/windows-view.md)窗口和目标窗口都可见。  
  
2.  从“搜索”菜单中选择“查找窗口”。  
  
     [“窗口搜索”对话框](../debugger/window-search-dialog-box.md)随即打开。  
  
    > [!TIP]
    >  若要减少屏幕的混乱，请选择“隐藏 Spy”选项。  此选项将隐藏 Spy\+\+ 主窗口，但仍将“窗口搜索”对话框显示在其他应用程序的前面。  单击“确定”或“取消”后，或者清除“隐藏 Spy\+\+”选项后，Spy\+\+ 主窗口将还原。  
  
3.  将“查找程序工具”拖到目标窗口上。  拖动该工具时，“窗口搜索”对话框将显示有关所选窗口的详细信息。  
  
     \- 或 \-  
  
     如果您知道所需窗口的句柄（例如，从调试器复制），则可以在“句柄”框中键入该句柄。  
  
     \- 或 \-  
  
     如果您知道所需窗口的标题和\/或类，则可以在“标题”和“类”文本框中键入它们，同时清除“句柄”文本框。  
  
4.  对于搜索的初始方向，选择“向上”或“向下”。  
  
5.  单击**“确定”**。  
  
     如果找到匹配的窗口，将在[窗口视图](../debugger/windows-view.md)窗口中突出显示该窗口。