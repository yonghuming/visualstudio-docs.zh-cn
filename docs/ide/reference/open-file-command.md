---
title: "“打开文件”命令 | Microsoft Docs"
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
  - "file.openfile"
helpviewer_keywords: 
  - "File.OpenFile 命令"
  - "属于命令"
  - "“打开文件”命令"
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “打开文件”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

打开现有文件并允许您指定编辑器。  
  
## 语法  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## 参数  
 `filename`  
 必选。  要打开的文件的完整路径或部分路径和文件名。  包含空格的路径必须引在引号中。  
  
## 开关  
 \/e:`editorname`  
 可选。  将在其中打开文件的编辑器的名称。  如果指定了参数，但未提供编辑器的名称，将出现**“打开方式”**对话框。  
  
 \/e:`editorname` 参数语法使用的编辑器的名称，则会出现并使用对话框，将括在引号中。  
  
 例如，若要在源代码编辑器中打开文件，可以为 \/e:`editorname` 参数输入以下内容。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 备注  
 当输入路径时，自动完成功能尝试定位正确的路径和文件名。  
  
## 示例  
 此示例将在源代码编辑器中打开样式文件“Test1.css”。  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [即时窗口](../../ide/reference/immediate-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)