---
title: "“启动”命令 | Microsoft Docs"
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
  - "debug.start"
helpviewer_keywords: 
  - "调试.启动命令"
  - "“启动”命令"
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “启动”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

开始调试启动项目。  
  
## 语法  
  
```  
Debug.Start [address]  
```  
  
## 参数  
 `address`  
 可选。  程序挂起执行的地址，类似于源代码中的断点。  此参数仅在调试模式下有效。  
  
## 备注  
 **Start** 命令在执行时会对指定的地址执行一个 RunToCursor 操作。  
  
## 示例  
 此示例启动调试器并忽略任何发生的异常。  
  
```  
>Debug.Start  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)