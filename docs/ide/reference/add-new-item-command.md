---
title: "“添加新项”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "project.addnewitem"
helpviewer_keywords: 
  - "“添加新项”命令"
  - "File.AddNewItem 命令"
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# “添加新项”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

将新的解决方案项（例如 .htm、.css、.txt 或框架集）添加到当前解决方案中并打开它。  
  
## 语法  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## 参数  
 `filename`  
 可选。  要添加到解决方案中的项的路径和文件名。  
  
## 开关  
 \/t: `templatename`  
 可选。  指定要创建的文件的类型。  如果未给出模板名称，默认情况下创建文本文件。  
  
 \/t:`templatename` 参数语法反映在**“添加新解决方案项”**对话框中找到的信息。  必须输入完整的类别并且后面带有文件类型，用反斜杠 \(`\`\) 将类别名称和文件类型分隔开，并用引号将整个字符串引起来。  
  
 例如，若要新建文本文件，则对于 \/t:`templatename` 参数可以输入以下内容。  
  
```  
/t:"General\Style Sheet"  
```  
  
 \/e: `editorname`  
 可选。  打开文件的编辑器的名称。  如果指定了参数，但未提供编辑器的名称，将出现**“打开方式”**对话框。  
  
 \/e:`editorname` 参数语法使用**“打开方式”对话框**中显示的编辑器名称，并将其名称引在引号中。  
  
 例如，若要在源代码编辑器中打开样式表，则对于 \/e:`editorname` 参数可以输入以下内容。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 示例  
 此示例将新的解决方案项 MyHTMLpg 添加到当前解决方案中。  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)