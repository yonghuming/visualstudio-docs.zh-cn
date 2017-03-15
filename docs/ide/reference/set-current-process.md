---
title: "设置当前进程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debug.SetCurrentProcess 命令"
  - "“设置当前进程”命令"
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# 设置当前进程
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

将指定的进程设置为调试器中的活动进程。  
  
## 语法  
  
```  
Debug.SetCurrentProcess index  
```  
  
## 实参  
 `index`  
 必需。  进程的索引。  
  
## 备注  
 调试时可以附加到多个进程，但在任何给定时间，调试器中只有一个进程处于活动状态。  您可以使用 `SetCurrentProcess` 命令设置活动进程。  
  
## 示例  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)