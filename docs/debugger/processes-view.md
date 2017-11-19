---
title: "进程视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.externaltools.spyplus.processesview
helpviewer_keywords: Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2ca6d0d7f875e376af37fcdcfa5d4156b8f4038
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="processes-view"></a>进程视图
进程视图显示你的系统上的所有活动进程树。 显示进程 ID 和模块名称。 如果你想要检查特定的系统进程，它通常对应于执行程序，请使用进程视图。 进程标识由模块名称，或者其指定为"系统 processes"。  
  
 Microsoft Windows 支持多个进程。 每个进程都可以有一个或多个线程和每个线程可以具有一个或多个关联的顶级窗口。 每个顶级窗口可以拥有一系列窗口。 一个 + 符号指示级别处于折叠状态。 在折叠的视图包含一个行，每个进程。 单击 + 符号来扩展该级别。  
  
 如果你想要检查特定的系统进程，它通常对应于执行程序，请使用进程视图。 进程标识由模块名称，或者其指定为"系统 processes"。 若要查找进程，折叠树和搜索列表。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-open-the-processes-view"></a>若要打开进程视图  
  
1.  从**Spy**菜单上，选择**进程**。  
  
 ![Spy &#43; &#43;进程视图](../debugger/media/spy--_processes.png "Spy + + _Processes")  
Spy++ 进程视图  
  
 上图显示了与进程和线程节点已展开的进程视图。  
  
### <a name="in-this-section"></a>本节内容  
 [进程视图中的进程搜索](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 说明如何在进程视图中查找特定的进程。  
  
 [显示进程属性](../debugger/how-to-display-process-properties.md)  
 说明如何显示一条消息有关的详细信息。  
  
### <a name="related-sections"></a>相关章节  
 [Spy++ 视图](../debugger/spy-increment-views.md)  
 说明 windows、 消息、 进程和线程 Spy + + 树视图。  
  
 [使用 Spy++](../debugger/using-spy-increment.md)  
 引入了 Spy + + 工具，并说明如何使用它。  
  
 [“进程搜索”对话框](../debugger/process-search-dialog-box.md)  
 用于查找特定的进程在进程视图中的节点。  
  
 [“进程属性”对话框](../debugger/process-properties-dialog-box.md)  
 显示在进程视图中选择的进程的属性。  
  
 [Spy++ 参考](../debugger/spy-increment-reference.md)  
 包含描述每个 Spy + + 菜单和对话框框中的部分。