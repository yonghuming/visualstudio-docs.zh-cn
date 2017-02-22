---
title: "“转到”命令 | Microsoft Docs"
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
  - "edit.goto"
helpviewer_keywords: 
  - "Debug.Goto 命令"
  - "“转到”命令"
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “转到”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

将光标移动到指定的行。  
  
## 语法  
  
```  
Edit.GoTo [linenumber]  
```  
  
## 参数  
 `linenumber`  
 可选。  表示要转到的行号的整数。  
  
## 备注  
 行号从 1 开始。  如果 `linenumber` 的值小于 1，则显示第一行。  如果 `linenumber` 的值大于最后一行的号码，则显示最后一行。  
  
 如果未指定 `linenumber` 的值，则显示**“转到行”**对话框。  
  
 此命令的别名是 GoToLn。  
  
## 示例  
  
```  
>Edit.GoTo 125  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)