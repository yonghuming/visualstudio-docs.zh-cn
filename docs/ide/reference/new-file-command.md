---
title: "“新建文件”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.newfile"
helpviewer_keywords: 
  - "File.NewFile 命令"
  - "“新建文件”命令"
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# “新建文件”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

创建新文件并打开它。  该文件出现在“杂项文件”文件夹下。  
  
## 语法  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## 参数  
 `filename`  
 可选。  文件名。  如果未提供名称，则使用默认名称。  如果未列出模板名称，则创建文本文件。  
  
## 开关  
 \/t:`templatename`  
 可选。  指定要创建的文件的类型。  
  
 \/t:`templatename` 参数语法反射在新文件 " 对话框中的信息。  输入类别名称，后跟反斜杠 \(`\`\)和模板名称，然后将整个字符串引在引号中。  
  
 例如，若要创建新的 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 源文件，可为 \/t:`templatename` 参数输入以下内容。  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 上面的示例指示“C\+\+ 文件”模板位于**“新建文件”**对话框中的 Visual C\+\+ 类别下。  
  
 \/e:`editorname`  
 可选。  将在其中打开文件的编辑器的名称。  如果指定了参数，但未提供编辑器的名称，将出现**“打开方式”**对话框。  
  
 \/e:`editorname` 参数语法使用的编辑器的名称，则会出现并使用对话框，将括在引号中。  
  
 例如，若要在源代码编辑器中打开文件，可以为 \/e:`editorname` 参数输入以下内容。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 示例  
 此示例将创建新的网页“test1.htm”，并在源代码编辑器中打开它。  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [即时窗口](../../ide/reference/immediate-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)