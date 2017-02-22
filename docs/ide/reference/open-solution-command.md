---
title: "“打开解决方案”命令 | Microsoft Docs"
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
  - "file.opensolution"
helpviewer_keywords: 
  - "File.OpenSolution 命令"
  - "“打开解决方案”命令"
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “打开解决方案”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

打开某个现有解决方案，关闭任何其他打开的解决方案。  
  
## 语法  
  
```  
File.OpenSolution filename  
```  
  
## 参数  
 `Filename`  
 必选。  要打开的解决方案的完整路径和文件名。  
  
 `filename` 参数的语法要求对包含空格的路径使用引号。  
  
## 备注  
 自动完成功能尝试在您键入时定位正确的路径和文件名。  
  
## 示例  
 此示例打开解决方案 Test1.sln。  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)