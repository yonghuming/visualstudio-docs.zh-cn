---
title: "如何： 在进程视图中的进程的搜索 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78c67ccc34d9c95914f6b46d537a4df3431c877f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>如何：在进程视图中搜索进程
你可以通过将其进程 ID 或模块字符串用作搜索条件搜索进程视图中的特定进程。 你还可以指定搜索的初始方向。 在对话框中的字段将显示所选进程的属性的过程树中。  
  
### <a name="to-search-for-a-process-in-processes-view"></a>要搜索进程视图中的进程  
  
1.  排列窗口，因此该 Spy + + 和活动[进程视图](../debugger/processes-view.md)是可见的窗口。  
  
2.  从**搜索**菜单上，选择**查找进程**  
  
     [进程搜索对话框](../debugger/process-search-dialog-box.md)打开。  
  
3.  键入的进程 ID 或模块字符串作为搜索条件。  
  
4.  清除不希望为其指定值的任何字段。  
  
    > [!TIP]
    >  若要查找的模块拥有的所有进程，请清除**过程**框中，键入中的模块名称**模块**框。 然后使用**查找下一个**继续搜索进程。  
  
5.  选择**向上**或**下**搜索的初始方向。  
  
6.  单击“确定”。  
  
 如果找不到匹配的进程，它以突出显示**进程视图**窗口。