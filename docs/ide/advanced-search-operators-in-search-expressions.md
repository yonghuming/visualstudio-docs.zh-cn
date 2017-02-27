---
title: "搜索表达式中的高级搜索运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Help Viewer 2.0, 搜索代码"
  - "Help Viewer 2.0, 按编程语言搜索代码"
  - "Help Viewer 2.0, 搜索关键字"
  - "Help Viewer 2.0, 搜索标题"
  - "搜索代码 [Help Viewer 2.0]"
  - "搜索标题 [Help Viewer 2.0]"
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 搜索表达式中的高级搜索运算符
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用更高级的搜索运算符，则可以通过创建从较简单类型而来的复杂的搜索表达式改善搜索内容。  如下表所示，这些运算符限制查询运行的上下文。  
  
> [!WARNING]
>  您必须输入带有最有一个冒号的搜索运算符，并在识别它们的搜索引擎的冒号之前不能有空格。  
  
|要搜索的|使用|示例|结果|  
|----------|--------|--------|--------|  
|一个主题标题的术语。|标题：|标题：BinaryReader|在其标题包含“BinaryReader”的主题。|  
|在代码示例中的术语|代码：|代码: readdouble|代码实例中包含“readdouble”的主题。|  
|一个在特定编程语言示例中的术语|代码: VB：|代码：VB：字符串|在 Visual Basic 示例中包含“字符串”的主题。|  
|一个与特定索引关键字关联的主题|关键字：|关键字: readbyte|与“ReadByte”索引关键字关联的主题。|  
  
 您可以使用代码：查找有关多个编程语言的任一一种的内容的运算符，但是它只为特定编程语言标记的内容返回结果。  下表列出了此运算符支持的编程语言：  
  
|编程语言|使用|  
|----------|--------|  
|Visual Basic|代码: VB<br /><br /> 或<br /><br /> 代码：visualbasic|  
|C\#|代码：c\#<br /><br /> 或<br /><br /> 代码: csharp|  
|C\+\+|代码: cpp<br /><br /> 或<br /><br /> 代码：C\+\+<br /><br /> 或<br /><br /> 代码: cplusplus|  
|F\#|代码：f\#<br /><br /> 或<br /><br /> 代码:fsharp|  
|JavaScript|代码：javascript<br /><br /> 或<br /><br /> 代码: js|  
|XAML|代码：xaml|  
  
## 请参阅  
 [搜索表达式中的逻辑运算符](../ide/logical-operators-in-search-expressions.md)   
 [全文搜索提示](../ide/full-text-search-tips.md)