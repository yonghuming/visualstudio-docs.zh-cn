---
title: "CA1046： 不要重载引用类型重载相等运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 344dfe7a4e35bf42e9e0a4efb2ca9bdf1b8f5d6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046：不要对引用类型重载相等运算符
|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或嵌套公共引用类型重载相等运算符。  
  
## <a name="rule-description"></a>规则说明  
 对于引用类型，相等运算符的默认实现几乎始终是正确的。 默认情况下，仅当两个引用指向同一对象时，它们才相等。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，删除相等运算符的实现。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，当引用类型的行为类似于内置值类型。 如果它是有意义执行加法或减法类型的实例上，则可能是正确实现相等运算符，并禁止显示冲突。  
  
## <a name="example"></a>示例  
 比较两个引用时，下面的示例演示默认行为。  
  
 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## <a name="example"></a>示例  
 下面的应用程序将某些引用进行比较。  
  
 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 本示例生成以下输出。  
  
 **= 新 (2，2) 和 b = 新 (2，2) 相等？不**  
**c 和相等？是的**  
**b 和 a 为 = =？不**  
**c 和 a 为 = =？是的**   
## <a name="related-rules"></a>相关的规则  
 [CA1013：重载加法方法和减法方法时重载相等运算符](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [相等运算符](/dotnet/standard/design-guidelines/equality-operators)