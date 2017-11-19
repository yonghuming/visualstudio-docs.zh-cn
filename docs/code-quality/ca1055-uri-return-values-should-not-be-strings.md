---
title: "CA1055: URI 返回值不应为字符串 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99ada3927275541e3b129c79bbcaac66f0aa5bdd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055：URI 返回值不应是字符串
|||  
|-|-|  
|TypeName|UriReturnValuesShouldNotBeStrings|  
|CheckId|CA1055|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 方法的名称包含"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"，并且该方法返回一个字符串。  
  
## <a name="rule-description"></a>规则说明  
 此规则将方法名称拆分为基于 Pascal 大小写约定的令牌，并检查每个令牌等于"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"。 如果没有匹配项，该规则将假定该方法返回的统一资源标识符 (URI)。 URI 的字符串表示形式容易导致分析和编码错误，并且可造成安全漏洞。 <xref:System.Uri?displayProperty=fullName>类以安全的方式提供这些服务。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将返回类型更改为<xref:System.Uri>。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果返回值不表示一个 URI。  
  
## <a name="example"></a>示例  
 下面的示例演示一种类型， `ErrorProne`，了违反此规则，并使用一种类型， `SaferWay`，满足该规则。  
  
 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1056：URI 属性不应是字符串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054：URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA2234：传递 System.Uri 对象，而不传递字符串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057：字符串 URI 重载调用 System.Uri 重载](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)