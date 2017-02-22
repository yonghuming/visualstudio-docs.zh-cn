---
title: "如何：显示用逗号分隔的项列表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 设置项集合格式"
  - "MSBuild, 用分号分隔项"
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：显示用逗号分隔的项列表
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) 中的项列表时，有时以易于阅读的方式显示这些项列表的内容很有用。  或者，您执行的任务可能用到以特殊的分隔符字符串分隔的项列表。  在这两种情况中，可以为项列表指定分隔符字符串。  
  
## 用逗号分隔列表中的项  
 默认情况下，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 用分号分隔列表中的项。  例如，请看一个含有以下值的 `Message` 元素：  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 当 `@(TXTFile)` 项列表包含项 App1.txt、App2.txt 和 App3.txt 时，消息为：  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 如果要更改默认行为，您可以指定自己的分隔符。  指定项列表分隔符的语法是：  
  
 `@(ItemListName, '<separator>')`  
  
 分隔符可以是单个字符或字符串，并且必须括在单引号中。  
  
#### 在项之间插入逗号和空格  
  
-   使用类似下面这样的项表示法：  
  
     `@(TXTFile, ', ')`  
  
## 示例  
 在此示例中，[Exec](../msbuild/exec-task.md) 任务运行 findstr 工具在文件 Phrases.txt 中查找指定的文本字符串。  在 findstr 命令中，文本搜索字符串由 **\/c:** 开关指示的，因此，`@(Phrase)` 项列表中的项之间插入项分隔符 `/c:`。  
  
 对于此示例，等效的命令行命令是：  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## 请参阅  
 [MSBuild 参考](../msbuild/msbuild-reference.md)   
 [项](../msbuild/msbuild-items.md)