---
title: "“列出线程”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listthreads"
helpviewer_keywords: 
  - "Debug.ListThreads 命令"
  - "“列出线程”命令"
  - "ListThreads 命令"
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “列出线程”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

显示当前程序中线程的列表。  
  
## 语法  
  
```  
Debug.ListThreads [index]  
```  
  
## 参数  
 `index`  
 可选。  通过线程的索引来选择要成为当前线程的线程。  
  
## 备注  
 如果指定 `index` 参数，它会将指定的线程标记为当前线程。  当前线程旁的列表中会显示一个星号 \(\*\)。  
  
## 示例  
  
```  
>Debug.ListThreads   
```  
  
## 请参阅  
 [“列出调用堆栈”命令](../../ide/reference/list-call-stack-command.md)   
 [“列出反汇编”命令](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)