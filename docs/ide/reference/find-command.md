---
title: "“查找”命令 | Microsoft Docs"
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
  - "edit.find"
helpviewer_keywords: 
  - "Edit.“查找”命令"
  - "“查找”命令"
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “查找”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

搜索文件使用选项的子集可用在 **查找和替换** 窗口的 **在文件中查找** 选项。  
  
## 语法  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## 参数  
 `findwhat`  
 必需。  要匹配的文本。  
  
## 开关  
 \/case 或 \/c  
 选项。  ，仅当大写和小写字母完全匹配。 `findwhat` 参数，指定的那些出现匹配项。  
  
 \/doc 或 \/d  
 选项。  搜索仅当前文件。  仅指定一个可用的搜索范围、 `/doc`、 `/proc`、 `/open`或 `/sel`。  
  
 \/markall 或 \/m  
 选项。  在包含在\+内搜索将匹配当前文件中的每一行放置一个图像。  
  
 \/open 或 \/o  
 选项。  搜索所有打开的文档，如同它们是文档。  仅指定一个可用的搜索范围、 `/doc`、 `/proc`、 `/open`或 `/sel`。  
  
 \/options 或 \/t  
 选项。  显示当前找到选项设置的列表，并执行搜索。  
  
 \/proc 或 \/p  
 选项。  只搜索当前过程。  仅指定一个可用的搜索范围、 `/doc`、 `/proc`、 `/open`或 `/sel`。  
  
 \/reset 或 \/e  
 选项。  返回查找选项到它们的默认设置，并且不执行搜索。  
  
 \/sel 或 \/s  
 选项。  只搜索当前选择。  仅指定一个可用的搜索范围、 `/doc`、 `/proc`、 `/open`或 `/sel`。  
  
 \/up 或 \/u  
 选项。  从当前位置的搜索头文件的开头的文件。  默认情况下，在文件中搜索和搜索的当前位置开始在文件的结尾。  
  
 \/regex 或 \/r  
 选项。  使用预定义在 `findwhat` 参数的特殊字符表示为文本模式而不是文本字符的表示形式。  有关完整的正则表达式的字符，请参见 [正则表达式](../../ide/using-regular-expressions-in-visual-studio.md)。  
  
 \/wild 或 \/l  
 选项。  使用预定义在 `findwhat` 参数的特殊字符作为表示法表示字符或字符序列。  
  
 \/word 或 \/w  
 选项。  只搜索全字。  
  
## 示例  
 此示例在代码中当前选定的部分执行区分大小写搜索 “somestring”这个词。  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## 请参阅  
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)