---
title: "CA1701： 资源字符串复合词应采用正确的大小写 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4dee5b21724944ea26e89c2cd1ace556f1377848
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701：资源字符串复合词应采用正确的大小写
|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1701|  
|类别|Microsoft.Naming|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 资源字符串包含似乎不正确的大小写的组合词。  
  
## <a name="rule-description"></a>规则说明  
 资源字符串中的每个单词拆分为根据大小写的令牌。 Microsoft 拼写检查器库会对由两个连续的标记构成的每个组合进行检查。 如果被识别，该单词将生成规则冲突。 导致冲突的复合词的示例包括"校验和"和"多部分"大小写应当为"Checksum"和"Multipart"，分别。 由于以前的常见用法，几个例外内置规则，并标记一些单个的词，例如"工具栏"和"Filename"，应作为两个不同的单词大小写。 在此示例中，将标记"工具栏"和"FileName"。  
  
 命名约定提供了通用的外观的库，面向公共语言运行时。 这减少了学习曲线，才能使用新的软件库和客户更有信心库由在开发的托管代码中有专业技能的人员。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 更改单词，使其具有正确的大小写。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果这两个部分的组合词都被拼写字典识别，目的是使用两个单词。  
  
 你还可以向拼写检查器的自定义字典添加组合词。 自定义字典中的单词不会导致冲突。 有关详细信息，请参阅[如何： 自定义代码分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1702：复合词应采用正确的大小写](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：标识符不应仅以大小写进行区分](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>另请参阅  
 [大小写约定](/dotnet/standard/design-guidelines/capitalization-conventions)   
 [命名规则](/dotnet/standard/design-guidelines/naming-guidelines)