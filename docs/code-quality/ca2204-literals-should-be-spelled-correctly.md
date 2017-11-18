---
title: "CA2204： 应正确拼写文本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords: CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7fca8484b3231a92ab3a425c4661229236833642
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204：应正确拼写文本
|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 与文本字符串用在参数或需要本地化的字符串和文本的字符串属性的方法传递包含一个或多个未被 Microsoft 拼写检查器库识别的单词。  
  
## <a name="rule-description"></a>规则说明  
 此规则检查的文本字符串，作为值传递给参数或属性时一个或多个以下情况下为真：  
  
-   <xref:System.ComponentModel.LocalizableAttribute>参数或属性的属性设置为 true。  
  
-   参数或属性名称包含"Text"、"消息"标题"。  
  
-   传递给 Console.Write 或 Console.WriteLine 方法将字符串参数的名称为"value"format"。  
  
 此规则将文本字符串解析成单词，将拆分为标记复合词，并检查每个单词/标记的拼写正确。 有关分析算法的信息，请参阅[CA1704： 标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
 默认情况下，为使用拼写检查器的英语 (en) 版本。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，更正该单词的拼写或添加到自定义词典的单词。 有关如何使用自定义词典的信息，请参阅[如何： 自定义代码分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 正确的拼写的单词可以减少所需的新软件库学习曲线。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703：资源字符串应正确拼写](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)