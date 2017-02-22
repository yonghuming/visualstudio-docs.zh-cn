---
title: "“符号路径”命令 | Microsoft Docs"
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
  - "debug.symbolpath"
helpviewer_keywords: 
  - "Debug.SymbolPath 命令"
  - "“符号路径”命令"
  - "SymbolPath 命令"
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “符号路径”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

设置调试器的目录列表，以搜索符号。  
  
## 语法  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## 实参  
 `pathname`  
 可选。  以分号分隔的调试器路径列表，用于搜索符号。  
  
## 备注  
 如果未指定 `pathname`，则该命令列出当前符号路径。  
  
## 示例  
 此示例将向符号目录列表中添加两个路径。  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## 示例  
 此示例显示以分号分隔的当前符号路径的列表。  
  
```  
Debug.SymbolPath  
```  
  
## 请参阅  
 [“命令”窗口](../../ide/reference/command-window.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)