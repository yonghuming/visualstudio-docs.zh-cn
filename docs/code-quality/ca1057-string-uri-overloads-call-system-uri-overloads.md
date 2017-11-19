---
title: "CA1057： 字符串 URI 重载调用 System.Uri 重载 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 094680be86955a47486ec108e779a313b7b0c0fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057：字符串 URI 重载调用 System.Uri 重载
|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 某个类型声明只是与字符串参数替换不同的方法重载<xref:System.Uri?displayProperty=fullName>参数，并且采用字符串参数的重载不调用采用的重载<xref:System.Uri>参数。  
  
## <a name="rule-description"></a>规则说明  
 因为重载差异仅在于字符串 /<xref:System.Uri>参数，则假定该字符串来表示统一资源标识符 (URI)。 URI 的字符串表示形式容易导致分析和编码错误，并且可造成安全漏洞。 <xref:System.Uri>类以安全的方式提供这些服务。 若要获得的好处<xref:System.Uri>类，字符串重载应调用<xref:System.Uri>重载使用字符串自变量。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 重新实现，因此，它将创建的实例使用的字符串表示形式的 URI 的方法<xref:System.Uri>类使用字符串自变量，并随后将传递<xref:System.Uri>对象的重载都<xref:System.Uri>参数。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果字符串参数不表示一个 URI。  
  
## <a name="example"></a>示例  
 下面的示例演示一个正确实现的字符串的重载。  
  
 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2234：传递 System.Uri 对象，而不传递字符串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1056：URI 属性不应是字符串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054：URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055：URI 返回值不应是字符串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)