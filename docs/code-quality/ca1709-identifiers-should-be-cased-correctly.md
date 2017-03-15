---
title: "CA1709：标识符的大小写应当正确 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldBeCasedCorrectly"
  - "CA1709"
helpviewer_keywords: 
  - "CA1709"
  - "IdentifiersShouldBeCasedCorrectly"
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 29
---
# CA1709：标识符的大小写应当正确
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|类别|Microsoft.Naming|  
|是否重大更改|间断 \- 如果是针对程序集、命名空间、类型、成员和参数引发的。<br /><br /> 无间断 \- 如果是针对泛型类型参数引发的。|  
  
## 原因  
 标识符名称的大小写不正确。  
  
 \- 或 \-  
  
 标识符的名称包含双字母的首字母缩略词，其中第二个字母为小写。  
  
 \- 或 \-  
  
 标识符的名称包含三个或更多大写字母的首字母缩略词。  
  
## 规则说明  
 命名约定为所有针对公共语言运行时的库提供了通用的外观。  这提高了学习新软件库的效率，并使客户进一步认为该软件库是由某位具有开发托管代码专门技术的人员所开发。  
  
 按照约定，参数名使用 Camel 大小写；命名空间、类型和成员名称使用 Pascal 大小写。  在采用 Camel 大小写格式的名称中，第一个字母为小写，名称中其他所有单词的第一个字母为大写。  Camel 大小写形式的名称示例为“packetSniffer”、“ioFile”和“fatalErrorCode”。  在采用 Pascal 大小写格式的名称中，第一个字母为大写，名称中其他所有单词的第一个字母为大写。  Pascal 大小写形式的名称示例为“PacketSniffer”、“IOFile”和“FatalErrorCode”。  
  
 该规则根据大小写将名称拆分为若干单词，并依据常见的双字母单词（例如“In”或“My”）列表来检查所有双字母单词。  如果未找到匹配项，则假定该单词是首字母缩略词。  此外，此规则假定发现一个首字母缩略词，其名称在一行中包含四个大写字母，或在名称的结尾发现一行中有三个大写字母。  
  
 按照约定，双字母的首字母缩略词全部使用大写字母，含三个或三个以上字符的首字母缩略词则使用 Pascal 大小写形式。  下面的示例使用该命名约定：“DB”、“CR”、“Cpa”和“Ecma”。  下面的示例与该约定冲突：“Io”、“XML”和“DoD”；对于非参数名称，冲突的示例有“xp”和“cpl”。  
  
 “ID”是一种导致与该规则冲突的特殊情况。'Id' 不是首字母缩略词，而是“identification”的缩写。  
  
## 如何解决冲突  
 更改名称，使其具有正确的大小写。  
  
## 何时禁止显示警告  
 如果您有自己的命名约定，或者此标识符表示正确的名称（如公司或技术的名称），则可以安全地禁止显示此警告。  
  
 您还可以向代码分析自定义词典中添加特定的术语、缩写和首字母缩写词。  在自定义词典中指定的词语将不会导致违反此规则。  有关更多信息，请参阅[如何：自定义代码分析字典](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)。  
  
## 相关规则  
 [CA1708：标识符不应仅以大小写进行区分](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)