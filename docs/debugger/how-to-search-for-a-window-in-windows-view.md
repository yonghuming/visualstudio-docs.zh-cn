---
title: "如何： 在窗口视图中的窗口搜索 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81b970979759c7ef6a6b236a1f2dff34815a72d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>如何：在窗口视图中搜索窗口
你可以通过将其句柄、 标题、 类或其标题和类的组合用作搜索条件来搜索特定窗口在窗口视图中。 你还可以指定搜索的初始方向。 在对话框中的字段将显示所选的窗口的属性的窗口树中。  
  
 使用已扩展到第二个级别 (所有 windows 桌面的子级)、 树启动，以便可以确定按类名和标题的桌面级窗口。 一旦你已选择桌面级窗口，你可以展开该级别以查找特定子窗口。  
  
### <a name="to-search-for-a-window-in-windows-view"></a>若要在窗口视图中窗口搜索  
  
1.  排列窗口，因此该 Spy + +， [Windows 视图](../debugger/windows-view.md)窗口中和目标窗口都可见。  
  
2.  从**搜索**菜单上，选择**查找窗口**。  
  
     [窗口搜索对话框](../debugger/window-search-dialog-box.md)打开。  
  
    > [!TIP]
    >  若要减少屏幕混乱，请选择**隐藏 Spy**选项。 此选项将隐藏主要的 Spy + + 窗口，并且仅留下**窗口搜索**对话框中显示在其他应用程序的前面。 Spy + + 主窗口将还原单击时**确定**或**取消**，或如果清除**隐藏 Spy + +**选项。  
  
3.  拖动**查找程序工具**目标范围内。 拖动该工具中，**窗口搜索**对话框显示有关所选的窗口的详细信息。  
  
     - 或 -  
  
     如果您知道所需的窗口的句柄 （例如，从调试器） 时，你可以键入在**处理**框。  
  
     - 或 -  
  
     如果你知道的标题和/或所需的窗口类，则可以键入在**标题**和**类**文本框中，然后清除**处理**文本框。  
  
4.  选择**向上**或**下**搜索的初始方向。  
  
5.  单击“确定”。  
  
     如果找到匹配的窗口，它以突出显示[Windows 视图](../debugger/windows-view.md)窗口。