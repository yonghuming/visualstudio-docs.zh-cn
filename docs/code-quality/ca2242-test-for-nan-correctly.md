---
title: "CA2242： 正确测试 NaN |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords: CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dd7f648880debe4b982d10e97aa7133419e0e840
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242：正确测试 NaN
|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 表达式对照测试某个值<xref:System.Single.NaN?displayProperty=fullName>或<xref:System.Double.NaN?displayProperty=fullName>。  
  
## <a name="rule-description"></a>规则说明  
 <xref:System.Double.NaN?displayProperty=fullName>这表示不数字时是不确定的算术运算, 的结果。 任何表达式，以便测试之间的值相等性和<xref:System.Double.NaN?displayProperty=fullName>始终返回`false`。 任何表达式，以便测试之间的值是否不相等和<xref:System.Double.NaN?displayProperty=fullName>始终返回`true`。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，并准确地确定某个值是否表示<xref:System.Double.NaN?displayProperty=fullName>，使用<xref:System.Single.IsNaN%2A?displayProperty=fullName>或<xref:System.Double.IsNaN%2A?displayProperty=fullName>测试该值。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示不正确地测试对值的两个表达式<xref:System.Double.NaN?displayProperty=fullName>和正确使用的表达式<xref:System.Double.IsNaN%2A?displayProperty=fullName>测试该值。  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]