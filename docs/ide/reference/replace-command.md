---
title: "Replace 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replace"
helpviewer_keywords: 
  - "Edit.Replace 命令"
  - "Replace 命令"
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Replace 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

替换文件中的文本使用选项的子集可用在 **查找和替换** 窗口的 **在文件中替换** 选项。  
  
## 语法  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
```  
  
## 参数  
 `findwhat`  
 必需。  要匹配的文本。  
  
 `replacewith`  
 必需。  用于替换的文本对于匹配的文本。  
  
## 开关  
 \/all 或 \/a  
 选项。  用替换文本替换搜索文本的所有匹配项。  
  
 \/case 或 \/c  
 选项。  ，在大写和小写字母完全匹配。 `findwhat` 参数时，指定的那些出现匹配项，则仅当。  
  
 \/doc 或 \/d  
 选项。  搜索仅当前文件。  仅指定一个可用的搜索范围、 `/doc`、 `/proc`、 `/open`或 `/sel`。  
  
 \/hidden 或 \/h  
 选项。  搜索隐藏的和折叠的文本，例如设计时控件的元数据，大纲显示的隐藏区域的文档或折叠的类或方法。  
  
 \/open 或 \/o  
 选项。  搜索所有打开的文档，如同它们是文档。  仅指定一个可用的搜索范围、 `/doc`、 `/proc`、 `/open`或 `/sel`。  
  
 \/options 或 \/t  
 选项。  显示当前找到选项设置的列表，并执行搜索。  
  
 \/proc 或 \/p  
 选项。  只搜索当前过程。  仅指定一个可用的搜索范围、 `/doc`、 `/proc`、 `/open`或 `/sel`。  
  
 \/regex 或 \/r  
 选项。  使用预定义在 `findwhat` 参数的特殊字符表示为文本模式而不是文本字符的表示形式。  有关完整的正则表达式的字符，请参见 [正则表达式](../../ide/using-regular-expressions-in-visual-studio.md)。  
  
 \/reset 或 \/e  
 选项。  返回查找选项到它们的默认设置，并且不执行搜索。  
  
 \/sel 或 \/s  
 选项。  只搜索当前选择。  仅指定一个可用的搜索范围、 `/doc`、 `/proc`、 `/open`或 `/sel`。  
  
 \/up 或 \/u  
 选项。  从当前位置的搜索在文件的顶部文件的。  默认情况下，在文件中搜索的当前位置开始和高级在文件的底部。  
  
 \/wild 或 \/l  
 选项。  使用预定义在 `findwhat` 参数的特殊字符作为表示法表示字符或字符序列。  
  
 \/word 或 \/w  
 选项。  只搜索全字。  
  
## 示例  
 此示例由所有的 `btnSubmit` 替换 `btnSend` 打开文档。  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## 请参阅  
 [查找和替换文本](../../ide/finding-and-replacing-text.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)