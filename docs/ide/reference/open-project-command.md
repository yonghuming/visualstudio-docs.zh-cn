---
title: "“打开项目”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openproject"
helpviewer_keywords: 
  - "File.OpenProject 命令"
  - "op 命令"
  - "“打开项目”命令"
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “打开项目”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

打开一个现有项目。  
  
## 语法  
  
```  
File.OpenProject filename  
```  
  
## 参数  
 `filename`  
 必选。  要打开的项目的完整路径和文件名。  
  
 `filename` 参数的语法要求对包含空格的路径使用引号。  
  
## 备注  
 自动完成功能尝试在您键入时定位正确的路径和文件名。  
  
 此命令在调试时不可用。  
  
## 示例  
 此示例将打开 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 项目 Test1。  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)