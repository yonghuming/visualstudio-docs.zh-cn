---
title: "“消息属性”对话框 | Microsoft Docs"
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
  - "消息选项"
  - "消息选项，常规"
ms.assetid: 58e9dc24-baf6-4ab8-916c-aea28b72e3b0
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “消息属性”对话框
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用此对话框可以查找有关特定消息的更多信息。  若要显示此对话框，请将焦点移动到[消息视图](../debugger/messages-view.md)窗口。  在树中选择任何消息节点，然后从“视图”菜单中选择“属性”。  
  
 此时只会显示“常规”选项卡。  下列设置可用：  
  
 **窗口句柄**  
 此窗口的唯一 ID。  窗口句柄编号会重复使用；它们只在窗口的生存期中标识该窗口。  单击此值可查看该窗口的属性。  
  
 **嵌套级别**  
 消息的嵌套深度，0 表示没有嵌套。  
  
 **消息**  
 所选窗口消息的编号、状态和名称。  
  
 **lResult**  
 *lResult* 参数的值（如果有）。  
  
 **wParam**  
 *wParam* 参数的值（如果有）。  
  
 **lParam**  
 *lParam* 参数的值（如果有）。  如果此值为指向字符串或结构的指针，则将对其解码。  
  
## 相关章节  
 [“消息选项”对话框](../debugger/message-options-dialog-box.md)  
 用于选择要在活动消息视图中列出的消息。  
  
 [“消息搜索”对话框](../debugger/message-search-dialog-box.md)  
 用于在消息视图中查找特定消息的节点。  
  
 [Spy\+\+ 参考](../debugger/spy-increment-reference.md)  
 包含描述各个 Spy\+\+ 菜单和对话框的章节。  
  
 [从查找窗口打开消息视图](_asug_choosing_message_options)  
 说明如何在“查找窗口”对话框中打开消息视图。  
  
 [在消息视图中搜索消息](../Topic/How%20to:%20Search%20for%20a%20Message%20in%20Messages%20View.md)  
 说明如何在消息视图中查找特定消息。  
  
 [消息视图](../debugger/messages-view.md)  
 显示与窗口、进程或线程关联的消息流。  
  
 [Spy\+\+ 视图](../debugger/spy-increment-views.md)  
 说明窗口、消息、进程和线程的 Spy\+\+ 树视图。  
  
 [使用 Spy\+\+](../debugger/using-spy-increment.md)  
 介绍 Spy\+\+ 工具并说明如何使用。