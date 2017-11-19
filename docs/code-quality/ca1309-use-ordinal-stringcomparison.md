---
title: "CA1309： 使用序号 StringComparison |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ba777ea4cd272a1392413a2ecbb52b9f45a3d71b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309：使用序号 StringComparison
|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 非的字符串比较运算不会设置<xref:System.StringComparison>参数为**序号**或**OrdinalIgnoreCase**。  
  
## <a name="rule-description"></a>规则说明  
 许多字符串运算，最重要<xref:System.String.Compare%2A?displayProperty=fullName>和<xref:System.String.Equals%2A?displayProperty=fullName>方法，现在提供接受的重载<xref:System.StringComparison?displayProperty=fullName>作为参数的枚举值。  
  
 当你指定**StringComparison.Ordinal**或**StringComparison.OrdinalIgnoreCase**，将非字符串比较。 即忽略了特定于自然语言的特性进行比较的决策时。 这意味着的决策基于简单字节比较，并忽略按区域性参数化的大小写或相等表。 因此，通过将参数显式设置为**StringComparison.Ordinal**或**StringComparison.OrdinalIgnoreCase**，你的代码通常获得速度，增加正确性，而且变成更可靠。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请将字符串比较方法更改为接受的重载<xref:System.StringComparison?displayProperty=fullName>枚举作为参数，并指定**序号**或**OrdinalIgnoreCase**。 例如，更改`String.Compare(str1, str2)`到`String.Compare(str1, str2, StringComparison.Ordinal)`。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 它是安全的库或应用程序旨在为有限的本地用户或应使用当前区域性的语义时禁止显示此规则的警告。  
  
## <a name="see-also"></a>另请参阅  
 [全球化警告](../code-quality/globalization-warnings.md)   
 [CA1307：指定 StringComparison](../code-quality/ca1307-specify-stringcomparison.md)