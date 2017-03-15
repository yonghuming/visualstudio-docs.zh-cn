---
title: "“列出源”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Debug.ListSource"
helpviewer_keywords: 
  - "Debug.ListSource 命令"
  - "“列出源”命令"
  - "ListSource 命令"
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# “列出源”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

显示源代码的指定行。  
  
## 语法  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## 开关  
 \/Count:`number`  
 可选。  指定要显示的行数。  
  
 \/Current  
 可选。  显示当前行。  
  
 \/File:`filename`  
 可选。  要显示的文件的路径。  如果未指定文件名，则该命令显示当前语句行的源代码。  
  
 \/Line:`number`  
 可选。  显示特定行号。  
  
 \/ShowLineNumbers:`yes|no`  
 可选。  指定是否显示行号。  
  
## 备注  
  
## 示例  
 此示例从文件 Form1.vb 的第 4 行列出源代码和可见的行号。  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)