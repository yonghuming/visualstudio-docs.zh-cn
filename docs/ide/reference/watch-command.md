---
title: "“监视”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.watch"
helpviewer_keywords: 
  - "Debug.Watch 命令"
  - "“监视”命令"
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# “监视”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

创建并打开**“监视”**窗口的指定实例。  可以使用**“监视”**窗口计算变量、表达式和寄存器的值，编辑这些值并保存结果。  
  
## 语法  
  
```  
Debug.Watch[index]  
```  
  
## 参数  
 `index`  
 必选。  监视窗口的实例编号。  
  
## 备注  
 `index` 必须是整数。  有效值为 1、2、3 或 4。  
  
## 示例  
  
```  
>Debug.Watch1  
```  
  
## 请参阅  
 [“自动”和“局部变量”窗口](../../debugger/autos-and-locals-windows.md)   
 [如何：在“变量”窗口中编辑值](../Topic/How%20to:%20Edit%20a%20Value%20in%20a%20Variable%20Window.md)   
 [如何：使用“快速监视”对话框](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)