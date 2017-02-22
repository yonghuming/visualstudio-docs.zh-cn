---
title: "“计算语句”命令 | Microsoft Docs"
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
  - "debug.evaluatestatement"
helpviewer_keywords: 
  - "Debug.EvaluateStatement 命令"
  - "“计算语句”命令"
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “计算语句”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

计算并显示给定的语句。  
  
## 语法  
  
```  
Debug.EvaluateStatement text   
```  
  
## 参数  
 `text`  
 必选。  要计算的语句。  
  
## 备注  
 用于输入 **EvaluateStatement** 命令的窗口确定等号 \(\=\) 是解释为比较运算符还是解释为赋值运算符。  
  
 在**“命令”**窗口中，将等号 \(\=\) 解释为比较运算符。  例如，如果变量 `a` 和 `b` 的值不同，则命令  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 将返回 `false` 值。  
  
 与此相反，在**“即时”**窗口中，将等号 \(\=\) 解释为赋值运算符。  例如，命令  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 将变量 `b` 的值赋值给变量 `a`。  
  
## 示例  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## 请参阅  
 [Print 命令](../../ide/reference/print-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)