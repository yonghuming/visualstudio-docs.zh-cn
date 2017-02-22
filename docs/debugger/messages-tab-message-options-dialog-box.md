---
title: "“消息选项”对话框 -&gt;“消息”选项卡 | Microsoft Docs"
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
  - "消息选项，消息"
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “消息选项”对话框 -&gt;“消息”选项卡
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用“消息”选项卡可以选择要在[消息视图](../debugger/messages-view.md)中列出的消息类型，并且可以指定消息搜索条件。  若要显示[“消息选项”对话框](../debugger/message-options-dialog-box.md)，请从“监视”菜单中选择“日志消息”。  
  
 通常，请先选择“消息组”，然后通过选择各个“要查看的消息”微调选择内容。  选择“全部”按钮将选择所有消息类型，选择“无”按钮将清除所有类型。  
  
 “消息”选项卡上提供了下列设置：  
  
 **要查看的消息**  
 选择要查看的特定消息。  如果创建了新的消息窗口，该窗口可以显示所有消息。  如果从“消息”选项卡筛选消息，则筛选器只会应用于新消息，不会应用于已在窗口视图中显示的消息。  
  
 **消息组**  
 选择要查看的消息组。  可用的组包括：  
  
-   WM\_USER：具有大于或等于 WM\_USER 的代码  
  
-   已注册：已使用 **RegisterWindowMessage** 调用注册  
  
-   未知：0 到 \(WM\_USER – 1\) 范围中的未知消息  
  
 请注意，这些“消息组”不会映射到“要查看的消息”下的特定项。  选择组时，该选项将直接应用到消息流。  
  
 “消息组”中的灰色复选框表示，已经为该组中的消息更改了“要查看的消息”列表框；未选择该组中的所有消息类型。  
  
 **保存为默认设置**  
 保存当前设置，供日后用作消息搜索选项。  退出 Spy\+\+ 时也将保存这些设置。