---
title: "CA2224： 重载相等运算符时重写 equals |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 44ba1c444d9348babcf07bfd807d6b0767bf3de9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224：重载相等运算符时重写 Equals 方法
|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 公共类型实现相等运算符，但不重写<xref:System.Object.Equals%2A?displayProperty=fullName>。  
  
## <a name="rule-description"></a>规则说明  
 相等运算符用于访问该功能的一种语法简便方式<xref:System.Object.Equals%2A>方法。 如果你实现了相等运算符，其逻辑必须是相同的<xref:System.Object.Equals%2A>。  
  
 如果代码违反此规则，C# 编译器会发出警告。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，应删除的相等运算符的实现，或重写<xref:System.Object.Equals%2A>并具有两个方法返回的相同值。 如果相等运算符不会引入的不一致的行为，则可以通过提供的实现来解决冲突<xref:System.Object.Equals%2A>调用<xref:System.Object.Equals%2A>基类中的方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果相等运算符将返回相同的值的继承的实现<xref:System.Object.Equals%2A>。 示例部分包含一类型，无法安全地禁止显示此规则的警告。  
  
## <a name="examples-of-inconsistent-equality-definitions"></a>不一致的相等性定义的示例  
  
### <a name="description"></a>描述  
 下面的示例演示具有相等定义不一致的类型。 `BadPoint`更改的相等性的含义，通过提供自定义实现相等运算符，但不重写<xref:System.Object.Equals%2A>以便行为相同。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## <a name="example"></a>示例  
 下面的代码测试的行为`BadPoint`。  
  
 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 本示例生成以下输出。  
  
 **= ([0] 1，1) 和 b = ([1] 2，2) 相等？不**  
**= = b？不**  
**a1 和 a 为等于？是的**  
**a1 = =？是的**  
**b 和 bcopy 相等？不**  
**b = = bcopy？是的**   
## <a name="example"></a>示例  
 下面的示例演示从技术上讲违反此规则，但不一致的方式的行为的类型。  
  
 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## <a name="example"></a>示例  
 下面的代码测试的行为`GoodPoint`。  
  
 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 本示例生成以下输出。  
  
 **= (1，1) 和 b = (2，2) 相等？不**  
**= = b？不**  
**a1 和 a 为等于？是的**  
**a1 = =？是的**  
**b 和 bcopy 相等？是的**  
**b = = bcopy？是的**   
## <a name="class-example"></a>类示例  
  
### <a name="description"></a>描述  
 下面的示例演示与该规则冲突的类 （引用类型）。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## <a name="example"></a>示例  
 下面的示例通过重写修复了冲突<xref:System.Object.Equals%2A?displayProperty=fullName>。  
  
 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## <a name="structure-example"></a>结构示例  
  
### <a name="description"></a>描述  
 下面的示例演示了违反此规则的结构 （值类型）。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## <a name="example"></a>示例  
 下面的示例通过重写修复了冲突<xref:System.ValueType.Equals%2A?displayProperty=fullName>。  
  
 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1046：不要对引用类型重载相等运算符](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225：运算符重载具有命名的备用项](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226：运算符应有对称重载](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218：重写 Equals 时重写 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231：重写 ValueType.Equals 时应重载相等运算符](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)