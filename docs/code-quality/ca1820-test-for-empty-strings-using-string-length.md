---
title: "CA1820： 测试是否有空字符串使用字符串长度 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bfacf70dd1d23d0596815ad2f9fa3f51986aaad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820：使用字符串长度测试是否有空字符串
|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 使用为空字符串比较字符串<xref:System.Object.Equals%2A?displayProperty=fullName>。  
  
## <a name="rule-description"></a>规则说明  
 比较字符串使用<xref:System.String.Length%2A?displayProperty=fullName>属性或<xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName>方法是使用比快很多<xref:System.Object.Equals%2A>。 这是因为<xref:System.Object.Equals%2A>执行以外的更多 MSIL 指令<xref:System.String.IsNullOrEmpty%2A>或执行要检索的指令数<xref:System.String.Length%2A>属性值和比较为零。  
  
 应该注意，<xref:System.Object.Equals%2A>和<xref:System.String.Length%2A>= = 0 具有不同的行为对于空字符串。 如果你尝试获取的值<xref:System.String.Length%2A>null 字符串的属性，公共语言运行时会引发<xref:System.NullReferenceException?displayProperty=fullName>。 如果执行一个 null 字符串和空字符串之间的比较时，公共语言运行时不会引发异常;比较返回`false`。 测试存在 null 不会显著影响这两种方法的相对性能。 如果目标[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，使用<xref:System.String.IsNullOrEmpty%2A>方法。 否则，请使用<xref:System.String.Length%2A>= = 比较尽可能。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请更改该比较以便使用<xref:System.String.Length%2A>属性和 null 字符串的测试。 如果面向[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，使用<xref:System.String.IsNullOrEmpty%2A>方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果性能不是问题。  
  
## <a name="example"></a>示例  
 下面的示例阐释用于查找一个空字符串的不同技术。  
  
 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]