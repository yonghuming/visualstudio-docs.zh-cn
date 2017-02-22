---
title: "“设置基数”命令 | Microsoft Docs"
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
  - "debug.setradix"
helpviewer_keywords: 
  - "Debug.SetRadix 命令"
  - "“设置基数”命令"
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “设置基数”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

设置或返回用于显示整型值的数字基数。  
  
## 语法  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## 参数  
 `10`、`16`、`hex` 或 `dec`  
 可选。  指示十进制（10 或 dec）或十六进制（16 或 hex）。  如果忽略此参数，则返回当前基数值。  
  
## 示例  
 此示例将环境设为以十六进制格式显示整型值。  
  
```  
>Debug.SetRadix hex  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)