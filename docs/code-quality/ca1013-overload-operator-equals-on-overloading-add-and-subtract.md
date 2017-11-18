---
title: "CA1013： 重载相等运算符的重载加法方法和减法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65f8802e0eb4e06466d5178b0af56753d537dd74
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013：重载加法方法和减法方法时重载相等运算符
|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 公共或受保护类型实现加或减运算符时没有实现相等运算符。  
  
## <a name="rule-description"></a>规则说明  
 类型的实例可以组合使用等加法和减法操作中，你几乎始终应定义相等，以便返回`true`的任何两个实例，具有相同的构成值。  
  
 相等运算符的重载实现中，不能使用默认的相等运算符。 这样将导致堆栈溢出。 若要实现相等运算符，请在实现使用 Object.Equals 方法。 请参见以下示例。  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```csharp  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，实现相等运算符，以便它与加法和减法运算符数学上一致。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，当相等运算符的默认实现提供正确的行为的类型。  
  
## <a name="example"></a>示例  
 下面的示例定义一个类型 (`BadAddableType`) 了违反此规则。 此类型应实现相等运算符以使具有相同的字段值测试任何两个实例`true`是否相等。 类型`GoodAddableType`显示的已更正的实现。 请注意，此类型还实现不等运算符，重写<xref:System.Object.Equals%2A>以满足其他规则。 此外将实现一个完整实现<xref:System.Object.GetHashCode%2A>。  
  
 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## <a name="example"></a>示例  
 下面的示例通过使用以前在本主题阐释相等运算符的默认和正确的行为中定义的类型的实例来测试相等性。  
  
 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 本示例生成以下输出。  
  
 **错误类型: {2，2} {2，2} 是否相等？不**  
**良好的类型: {3，3} {3，3} 是否相等？是的**  
**良好的类型: {3，3} {3，3} 包括 = =？ 是的**  
**错误类型: {2，2} {9,9} 相等？不**  
**良好的类型: {3，3} {9,9} 包括 = =？ 不**   
## <a name="see-also"></a>另请参阅  
 [相等运算符](/dotnet/standard/design-guidelines/equality-operators)