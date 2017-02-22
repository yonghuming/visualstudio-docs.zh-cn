---
title: "“添加现有项”命令 | Microsoft Docs"
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
  - "project.addexistingitem"
helpviewer_keywords: 
  - "“添加现有项”命令"
  - "File.AddExistingItem 命令"
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “添加现有项”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

将现有文件添加到当前解决方案中并打开它。  
  
## 语法  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## 参数  
 `filename`  
 必选。  要添加到当前解决方案的项的完整路径和文件名，并带有扩展名。  如果文件路径或文件名包含空格，请用引号将整个路径引起来。  
  
## 开关  
 \/e: `editorname`  
 可选。  将在其中打开文件的编辑器的名称。  如果指定了参数，但未提供编辑器的名称，将出现**“打开方式”**对话框。  
  
 \/e:`editorname` 参数语法使用**“打开方式”对话框**中显示的编辑器名称，并将其名称引在引号中。  例如，若要在源代码编辑器中打开样式表，则对于 \/e:`editorname` 参数可以输入以下内容。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 备注  
 自动完成功能尝试在您键入时定位正确的路径和文件名。  
  
## 示例  
 此示例将 Form1.frm 文件添加到当前解决方案中。  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)