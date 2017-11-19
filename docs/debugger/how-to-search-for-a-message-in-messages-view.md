---
title: "如何： 搜索消息视图中的某个消息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36c3158542dff52a2e1ca350e49be254219183c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>如何：在消息视图中搜索消息
你可以通过将其句柄、 类型或消息 ID 用作搜索条件搜索在消息视图中的特定消息。 上述任一 — 或组合 — 将有效的搜索条件。 也可以指定搜索的初始方向。 在对话框中的字段预加载了当前所选消息的属性。  
  
### <a name="to-search-for-a-message-in-messages-view"></a>若要搜索的消息在消息视图  
  
1.  排列窗口，因此该 Spy + + 和活动[消息视图](../debugger/messages-view.md)是可见的窗口。  
  
2.  从**搜索**菜单上，选择**查找消息**。  
  
     [消息搜索对话框](../debugger/message-search-dialog-box.md)打开。  
  
3.  拖动**查找程序工具**所需的范围内。 拖动该工具中，**消息搜索**对话框显示有关所选的窗口的详细信息。  
  
     - 或 -  
  
     如果你想要检查其消息的窗口的句柄，则键入到**处理**文本框。  
  
     - 或 -  
  
     如果你知道的消息类型和/或所需的消息 ID，将其从选定**类型**和**消息**下拉列表菜单，然后清除**处理**文本框。  
  
4.  清除不希望为其指定值的任何字段。  
  
    > [!TIP]
    >  若要减少屏幕混乱，请选择**隐藏 Spy**选项。 此选项将隐藏 Spy + + 主窗口，但仅仍**查找窗口**对话框中显示在其他应用程序的前面。 Spy + + 主窗口将还原单击时**确定**或**取消**，或如果清除**隐藏 Spy + +**选项。  
  
5.  选择**向上**或**下**搜索的初始方向。  
  
6.  单击“确定”。  
  
 如果找到匹配的消息时，它将突出显示在消息视图窗口中。 请参阅[消息视图](../debugger/messages-view.md)。