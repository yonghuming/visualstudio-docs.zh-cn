---
title: "“列出寄存器”命令 | Microsoft Docs"
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
  - "debug.listregisters"
helpviewer_keywords: 
  - "Debug.ListRegisters 命令"
  - "“列出寄存器”命令"
  - "ListRegisters 命令"
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “列出寄存器”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

显示选定寄存器的值，使您可以修改要显示的寄存器的列表。  
  
## 语法  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## 开关  
 \/显示 \[{`register`&#124;`registerGroup`}...\]  
 显示指定的 `register` 或 `registerGroup` 的值。  如果未指定 `register` 或 `registerGroup`，则显示默认的寄存器列表。  如果未指定开关，则行为相同。  例如：  
  
 `Debug.ListRegisters /Display eax`  
  
 等效于  
  
 `Debug.ListRegisters eax`  
  
 \/List  
 显示列表中的所有寄存器组。  
  
 \/Watch \[{`register`&#124;`registerGroup`}...\]  
 向列表中添加一个或多个 `register` 或 `registerGroup` 值。  
  
 \/Unwatch \[{`register`&#124;`registerGroup`}...\]  
 从列表中移除一个或多个 `register` 或 `registerGroup` 值。  
  
## 备注  
 可以使用别名 `r` 替换 `Debug.ListRegisters`。  
  
## 示例  
 此示例使用 `Debug.ListRegisters` 的别名 `r` 显示寄存器组 `Flags` 的值。  
  
```  
r /Display Flags  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [调试基础知识：“寄存器”窗口](../../debugger/debugging-basics-registers-window.md)   
 [如何：使用“寄存器”窗口](../../debugger/how-to-use-the-registers-window.md)