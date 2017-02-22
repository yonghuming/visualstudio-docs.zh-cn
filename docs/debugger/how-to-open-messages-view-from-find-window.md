---
title: "如何：从查找窗口打开消息视图 | Microsoft Docs"
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
  - "Spy++ 中的消息视图，打开"
  - "打开 Spy++ 中的消息视图"
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：从查找窗口打开消息视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可能会发现使用“查找窗口”对话框选择目标窗口，然后打开该窗口的消息视图非常方便。  
  
### 使用“查找窗口”对话框打开消息视图窗口  
  
1.  排列窗口，以便 Spy\+\+ 和目标窗口都可见。  
  
2.  从“监视”菜单中选择“查找窗口”。  
  
     [“查找窗口”对话框](../debugger/find-window-dialog-box.md)随即打开。  
  
3.  从“窗口”选项卡中，将“查找程序工具”拖到目标窗口上。  拖动该工具时，“查找窗口”对话框将显示所选窗口的详细信息。  
  
     \- 或 \-  
  
     如果您具有要检查的窗口的句柄（例如，从调试器复制），则可以在“句柄”文本框中键入该句柄。  
  
4.  在“显示”之下，选择“消息”。  
  
5.  按**“确定”**。  
  
     随即打开一个空白[消息视图](../debugger/messages-view.md)窗口，并向 Spy\+\+ 工具栏添加了“消息”菜单。  
  
6.  从“消息”菜单中选择“记录选项”。  
  
     [“消息选项”对话框](../debugger/message-options-dialog-box.md)随即打开。  
  
7.  为要显示的消息选择选项。  
  
8.  按“确定”开始记录消息。  
  
     根据所选的选项，消息开始流入活动的消息视图窗口。  
  
9. 当您得到足够多的消息后，从“消息”菜单中选择“停止记录”。