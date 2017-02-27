---
title: "CA2204：应正确拼写文本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Literals should be spelled correctly"
  - "CA2204"
  - "LiteralsShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA2204"
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2204：应正确拼写文本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 将字符串传递到需要在本地化字符串的参数或属性中使用之处的方法，该字符串包含一个或多个未被 Microsoft 拼写检查器库识别的单词。  
  
## 规则说明  
 此规则检查原义字符串，在一个或多个以下的情况下为 true 时，其作为值传递给参数或属性：  
  
-   参数或属性的 <xref:System.ComponentModel.LocalizableAttribute> 特性设置为 true。  
  
-   参数或属性名称包含“文本”、“消息”或“标题”。  
  
-   对 Console.Write 或 Console.WriteLine 方法传递的字符串参数的名称是“值”或者“格式”。  
  
 此规则将文本字符串解析为单词、将组合词拆分为标记并检查每个单词\/标记的拼写。  有关解析算法的信息，请参见[CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
 默认情况下，使用拼写检查器的英语 \(en\) 版本。  
  
## 如何解决冲突  
 若要修复与此规则的冲突，请更正单词的拼写，或者将单词添加到自定义字典中。  有关如何使用自定义词典的信息，请参见[如何：自定义代码分析字典](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  拼写正确的单词可以减少新软件库所需的学习曲线。  
  
## 相关规则  
 [CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703：资源字符串应正确拼写](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)