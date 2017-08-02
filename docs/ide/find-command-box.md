---
title: "“查找/命令”框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findcommandbox"
helpviewer_keywords: 
  - "“查找/命令”框"
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# “查找/命令”框
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以搜索文本并运行该 **查找\/命令** 框的 Visual Studio 命令。  默认情况下 **查找\/命令** 框可用作工具栏控件，但是，不再可见。  通过选择在 **标准** 工具栏的 **添加或删除按钮** 然后选择 **查找**显示 **查找\/命令** 框。  
  
 若要运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令，比 \(\>\) 符号请开头它与一大。  
  
 **“查找\/命令”**框保留输入的最后 20 项，并将它们显示在下拉列表中。  可以浏览该列表中选择箭头键。  
  
 ![“查找&#47;命令”框](~/ide/media/findcommandbox.png "FindCommandBox")  
“查找\/命令”框  
  
## 搜索文本  
 默认情况下，那么，当您在 **查找\/命令** 框中指定文本然后选择 enter 键时，Visual Studio 搜索当前文件或工具窗口使用在 **在文件中查找** 对话框中指定的选项。  有关详细信息，请参阅 [查找和替换文本](../ide/finding-and-replacing-text.md)。  
  
## 输入命令  
 若要使用 **查找\/命令** 框发出一个 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令或别名而不是搜索文本，比 \(\>\) 符号输入 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 顺序，开头。一大。  例如：  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 或者，也可以使用“命令”窗口输入和执行单个或多个命令。  一些命令或别名可单独输入并执行，而另一些命令的语法则要求有参数。  有关带参数的命令的列表，请参见 [Visual Studio 命令](../ide/reference/visual-studio-commands.md)。  
  
## 转义符  
 命令行中的插入符号 \(^\) 字符表示紧随其后的字符将按原义而不作为控制字符进行解释。  这可用于在参数或开关值（开关名除外）中嵌入直引号 \("\)、空格、正斜杠、插入符号或其他任何字符。  例如，  
  
```  
>Edit.Find ^^t /regex  
```  
  
 插入符号在引号内或引号外的作用相同。  如果插入符号是该行的最后一个字符，则忽略不计。  
  
## 请参阅  
 [“命令”窗口](../ide/reference/command-window.md)   
 [查找和替换文本](../ide/finding-and-replacing-text.md)