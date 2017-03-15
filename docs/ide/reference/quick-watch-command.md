---
title: "“快速监视”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.quickwatch"
helpviewer_keywords: 
  - "Debug.Quickwatch 命令"
  - "“快速监视”命令"
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# “快速监视”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

显示在[“快速监视”对话框](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)的“表达式”字段中选定或指定的文本。  可以使用此对话框计算调试器所识别的变量或表达式的当前值或者寄存器的内容。  另外，可以更改任何非常数变量的值或任何寄存器的内容。  
  
## 语法  
  
```  
Debug.QuickWatchq [text]  
```  
  
## 参数  
 `text`  
 可选。  要添加到**“快速监视”**对话框中的文本。  
  
## 备注  
 如果省略 `text`，在光标处的当前选定文本或单词将添加到“监视”窗口中。  
  
## 示例  
  
```  
>Debug.QuickWatch  
```  
  
## 请参阅  
 [如何：使用“快速监视”对话框](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)