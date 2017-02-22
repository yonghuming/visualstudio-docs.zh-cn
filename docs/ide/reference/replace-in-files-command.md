---
title: "“在文件中替换”命令 | Microsoft Docs"
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
  - "edit.replaceinfiles"
helpviewer_keywords: 
  - "Edit.ReplaceInFiles 命令"
  - "“在文件中替换”命令"
  - "ReplaceInFiles 命令"
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “在文件中替换”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

替换文件中的文本使用选项的子集可用在 **查找和替换** 窗口的 **在文件中替换** 选项。  
  
## 语法  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
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
  
 \/ext: `extensions`  
 选项。  指定文件扩展名必须要搜索的文件。  
  
 \/keep 或 \/k  
 选项。  指定所有已更改的文件将打开。  
  
 \/lookin: `searchpath`  
 选项。  搜索的目录。  如果路径包含空格，则将整个路径放在引号内。  
  
 \/options 或 \/t  
 选项。  显示当前找到选项设置的列表，并执行搜索。  
  
 \/regex 或 \/r  
 选项。  使用预定义在 `findwhat` 参数的特殊字符表示为文本模式而不是文本字符的表示形式。  有关完整的正则表达式的字符，请参见 [正则表达式](../../ide/using-regular-expressions-in-visual-studio.md)。  
  
 \/reset 或 \/e  
 选项。  返回查找选项到它们的默认设置，并且不执行搜索。  
  
 \/stop  
 选项。  ，如果一个正在进行，则暂停当前搜索操作。  ，当 `/stop`指定后，替换忽略其他参数。  例如，停止当前替换应输入以下内容:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 \/sub 或 \/s  
 选项。  搜索在 \/lookin 中指定的目录中的子文件夹中:`searchpath` 参数。  
  
 \/text2 或 \/2  
 选项。  该图标的结果。 **查找结果 2** 窗口中。  
  
 \/wild 或 \/l  
 选项。  使用预定义在 `findwhat` 参数的特殊字符作为表示法表示字符或字符序列。  
  
 \/word 或 \/w  
 选项。  只搜索全字。  
  
## 示例  
 此示例搜索 `btnCancel` 并用在位于文件夹下的所有 .cls 文件的 `btnReset` 替换了 “我的 visual studio 项目”并在 **查找结果 2** 窗口的交换信息。  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## 请参阅  
 [查找和替换文本](../../ide/finding-and-replacing-text.md)   
 [在文件中替换](../../ide/replace-in-files.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)