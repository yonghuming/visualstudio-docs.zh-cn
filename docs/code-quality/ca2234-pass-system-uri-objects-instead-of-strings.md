---
title: "CA2234： 传递 System.Uri 对象，而不是字符串 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99001a5406ce4e70e0e76670eba250073ce030b2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234：传递 System.Uri 对象，而不传递字符串
|||  
|-|-|  
|TypeName|PassSystemUriObjectsInsteadOfStrings|  
|CheckId|CA2234|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 具有名称中包含"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"; 一个字符串参数的方法进行调用和方法的声明类型包含具有的对应方法重载<xref:System.Uri?displayProperty=fullName>参数。  
  
## <a name="rule-description"></a>规则说明  
 参数名称拆分为基于 camel 大小写约定的标记，然后检查每个令牌以确定它是否等于"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"。 如果没有匹配项，则假定该参数表示统一资源标识符 (URI)。 URI 的字符串表示形式容易导致分析和编码错误，并且可造成安全漏洞。 <xref:System.Uri>类以安全的方式提供这些服务。 在不同的表示形式的 URI 方面的两种重载之间存在一个选择时，用户应该选择采用的重载<xref:System.Uri>自变量。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，调用的重载采用<xref:System.Uri>自变量。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果字符串参数不表示一个 URI。  
  
## <a name="example"></a>示例  
 下面的示例演示一种方法， `ErrorProne`，这违反了规则和方法， `SaferWay`，从而正确调用<xref:System.Uri>重载。  
  
 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1057：字符串 URI 重载调用 System.Uri 重载](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)  
  
 [CA1056：URI 属性不应是字符串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054：URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055：URI 返回值不应是字符串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)