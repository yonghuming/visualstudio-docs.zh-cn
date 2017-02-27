---
title: "“切换断点”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.togglebreakpoint"
helpviewer_keywords: 
  - "Debug.ToggleBreakPoint 命令"
  - "“切换断点”命令"
  - "ToggleBreakpoint 命令"
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# “切换断点”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在文件的当前位置，根据其当前状态打开或关闭断点。  
  
## 语法  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## 参数  
 `text`  
 可选。  如果指定文本，则该行标记为命名断点。  否则，该行标记为未命名断点，它类似于按 F9 键时所发生的操作。  
  
## 示例  
 下面的示例将切换当前断点。  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)