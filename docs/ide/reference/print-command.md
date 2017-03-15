---
title: "Print 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.print"
helpviewer_keywords: 
  - "Debug.Print 命令"
  - "Print 命令"
  - "Print 方法"
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Print 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

计算表达式或显示指定的文本。  
  
## 语法  
  
```  
Debug.Print text  
```  
  
## 参数  
 `text`  
 必选。  要计算的表达式或者要显示的文本。  
  
## 备注  
 可以将问号 \(?\) 用作此命令的别名。  例如，命令  
  
```  
>Debug.Print expA  
```  
  
 也可以写为  
  
```  
>? expA  
```  
  
 此命令的两个版本都返回表达式 `expA` 的当前值。  
  
## 示例  
  
```  
>Debug.Print varA  
```  
  
## 请参阅  
 [“计算语句”命令](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)