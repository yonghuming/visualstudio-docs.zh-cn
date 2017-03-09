---
title: "CA1702：复合词应采用正确的大小写 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
helpviewer_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1702：复合词应采用正确的大小写
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|类别|Microsoft.Naming|  
|是否重大更改|间断 \- 如果对程序集引发。<br /><br /> 无间断 \- 如果对类型参数引发。|  
  
## 原因  
 标识符的名称包含多个单词，其中至少有一个单词显示为大小写不正确的组合词。  
  
## 规则说明  
 标识符的名称根据大小写被拆分成几个单词。  每两个连续的单词组合由 Microsoft 拼写检查器库进行检查。  如果它被识别，该标识符将生成规则冲突。  导致冲突的复合词示例包括“CheckSum”和“MultiPart”，它们的大小写分别应为“Checksum”和“Multipart”。  由于以前经常使用，规则中置入了一些特例，一些单个的词也会被标记，例如“Toolbar”和“Filename”，应按照大小写规则将它们视为两个不同的单词（即“ToolBar”和“FileName”）。  
  
 命名约定为所有针对公共语言运行时的库提供了通用的外观。  这提高了学习新软件库的效率，并使客户进一步认为该软件库是由某位具有开发托管代码专门技术的人员所开发。  
  
## 如何解决冲突  
 更改名称，使其具有正确的大小写。  
  
## 何时禁止显示警告  
 如果复合词的两部分都被拼写字典识别，而目的是使用两个单词，则可以安全地禁止显示此规则发出的警告。  
  
## 相关规则  
 [CA1701：资源字符串复合词应采用正确的大小写](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：标识符不应仅以大小写进行区分](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## 请参阅  
 [命名准则](../Topic/Naming%20Guidelines.md)   
 [大小写约定](../Topic/Capitalization%20Conventions.md)