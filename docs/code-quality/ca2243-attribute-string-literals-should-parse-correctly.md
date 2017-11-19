---
title: "CA2243： 字符串应正确分析特性文本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3ec86725873f5724609f411072dab4a4bde9d990
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243：应正确分析特性字符串文本
|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 有关 URL、 GUID 或版本不能正确解析属性字符串文本参数。  
  
## <a name="rule-description"></a>规则说明  
 由于属性派生自<xref:System.Attribute?displayProperty=fullName>，和特性在编译时，仅常量的值可以传递给其构造函数。 必须表示 Url、 Guid 和版本的属性参数不能类型化为<xref:System.Uri?displayProperty=fullName>， <xref:System.Guid?displayProperty=fullName>，和<xref:System.Version?displayProperty=fullName>，因为这些类型不能表示为常量。 相反，它们必须由字符串表示。  
  
 由于参数被类型化为一个字符串，所以有可能，无法在编译时传递一个格式不正确的参数。  
  
 此规则使用命名的启发式方法来查找表示统一资源标识符 (URI)，全局唯一标识符 (GUID) 或版本的参数，并验证传递的值正确。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 将参数字符串更改为格式正确的 URL、 GUID 或版本。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果参数不表示 URL、 GUID 或版本。  
  
## <a name="example"></a>示例  
 下面的示例显示与该规则冲突 AssemblyFileVersionAttribute 代码。  
  
 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 由以下触发规则：  
  
-   包含版本，无法被分析为 System.Version 的参数。  
  
-   包含 guid，无法被分析为 System.Guid 的参数。  
  
-   包含 uri、 urn 或 url，无法被分析为 System.Uri 参数。  
  
## <a name="see-also"></a>另请参阅  
 [CA1054：URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)