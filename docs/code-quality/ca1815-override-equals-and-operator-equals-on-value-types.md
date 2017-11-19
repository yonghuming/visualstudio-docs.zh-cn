---
title: "CA1815： 重写 equals 和相等运算符的值类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 20b31e4ea20fd3d1a4ec254507962bf4e8946bb4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815：重写值类型上的 Equals 和相等运算符
|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 公共值类型不会覆盖<xref:System.Object.Equals%2A?displayProperty=fullName>，或未实现相等运算符 （= =）。 此规则不会检查枚举。  
  
## <a name="rule-description"></a>规则说明  
 对于值类型，继承的实现<xref:System.Object.Equals%2A>使用反射库，并比较所有字段的内容。 反射需要消耗大量计算资源，可能没有必要比较每一个字段是否相等。 如果你指望用户能比较或排序的实例，或将其用作哈希表键，则值类型应实现<xref:System.Object.Equals%2A>。 如果您的编程语言支持运算符重载，你还应提供相等和不相等运算符的实现。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，提供的实现<xref:System.Object.Equals%2A>。 如果你知道如何操作，实现相等运算符。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果值类型的实例将不会彼此比较。  
  
## <a name="example-of-a-violation"></a>冲突的示例  
  
### <a name="description"></a>描述  
 下面的示例演示了违反此规则的结构 （值类型）。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>修复方法的示例  
  
### <a name="description"></a>描述  
 下面的示例通过重写修复前面的冲突<xref:System.ValueType.Equals%2A?displayProperty=fullName>和实现相等运算符 (= =、 ！ =)。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2224：重载相等运算符时重写 Equals 方法](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231：重写 ValueType.Equals 时应重载相等运算符](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226：运算符应有对称重载](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Object.Equals%2A?displayProperty=fullName>