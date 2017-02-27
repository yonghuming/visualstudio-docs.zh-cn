---
title: "CA1703：资源字符串应正确拼写 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ResourceStringsShouldBeSpelledCorrectly"
  - "CA1703"
helpviewer_keywords: 
  - "CA1703"
  - "ResourceStringsShouldBeSpelledCorrectly"
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1703：资源字符串应正确拼写
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|类别|Microsoft.Naming|  
|是否重大更改|非重大更改|  
  
## 原因  
 资源字符串包含一个或多个未被 Microsoft 拼写检查器库识别的单词。  
  
## 规则说明  
 此规则将资源字符串解析为单词（将组合词拆分为标记）并检查每个单词\/标记的拼写。  有关解析算法的信息，请参见[CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
 默认情况下，使用拼写检查器的英语 \(en\) 版本。  
  
## 如何解决冲突  
 若要修复与此规则的冲突，请使用拼写正确的完整单词，或者将单词添加到自定义字典中。  有关如何使用自定义词典的信息，请参见[CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  拼写正确的单词可以减少学习新软件库所需的时间。  
  
## 相关规则  
 [CA1701：资源字符串复合词应采用正确的大小写](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204：应正确拼写文本](../code-quality/ca2204-literals-should-be-spelled-correctly.md)