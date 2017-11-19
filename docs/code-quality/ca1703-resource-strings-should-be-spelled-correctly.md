---
title: "CA1703： 资源字符串应正确拼写 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c7828aa218933208408a285510e998921d6f032
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703：资源字符串应正确拼写
|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|类别|Microsoft.Naming|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 资源字符串包含一个或多个未被 Microsoft 拼写检查器库识别的单词。  
  
## <a name="rule-description"></a>规则说明  
 此规则将资源字符串解析为单词 （词汇切分复合词），并检查每个单词/标记的拼写正确。 有关分析算法的信息，请参阅[CA1704： 标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
 默认情况下，为使用拼写检查器的英语 (en) 版本。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，使用全字拼写正确，或将字添加到自定义词典。 有关如何使用自定义词典的信息，请参阅[CA1704： 标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 正确的拼写的单词可以减少了解新的软件库所需的时间。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1701：资源字符串复合词应采用正确的大小写](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1704：标识符应正确拼写](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204：应正确拼写文本](../code-quality/ca2204-literals-should-be-spelled-correctly.md)