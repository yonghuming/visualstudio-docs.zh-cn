---
title: "CA2233： 运算不应溢出 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d8b602d83eee4be49f63eef0ee8d2cd3d77f5040
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233：运算不应溢出
|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 某个方法执行的算术运算，并且不会验证操作数事先以防止溢出。  
  
## <a name="rule-description"></a>规则说明  
 如果未首先验证操作数，以确保操作的结果不涉及的数据类型的可能值的范围之外，应执行算术运算。 具体取决于执行上下文和涉及的数据类型，算术溢出可能导致<xref:System.OverflowException?displayProperty=fullName>或放弃结果的最高有效位。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请在执行该操作之前验证操作数。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果操作数的可能的值将永远不会导致算术运算溢出。  
  
## <a name="example-of-a-violation"></a>冲突的示例  
  
### <a name="description"></a>描述  
 下面的示例中的方法操作违反了此规则的整数。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]需要**删除**整数溢出选项禁用此激发。  
  
### <a name="code"></a>代码  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### <a name="comments"></a>注释  
 如果在此示例中该方法传递<xref:System.Int32.MinValue?displayProperty=fullName>，则操作将下溢。 这将导致丢弃的结果的最高有效位。 下面的代码演示如何发生这种情况。  
  
 [C#]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 [VB]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### <a name="output"></a>输出  
  
```  
2147483647  
```  
  
## <a name="fix-with-input-parameter-validation"></a>修复的输入的参数验证  
  
### <a name="description"></a>描述  
 下面的示例通过验证输入的值来修复前面的冲突。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]  
  
## <a name="fix-with-a-checked-block"></a>修复已选中块  
  
### <a name="description"></a>描述  
 下面的示例通过检查块中包装该操作来修复前面的冲突。 如果该操作会导致溢出，<xref:System.OverflowException?displayProperty=fullName>将引发。  
  
 请注意，已选中的块不支持在[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]  
  
## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>开启检查算术上溢/下溢  
 如果你打开检查算术上溢/下溢 C# 中，它等效于在选中的块中包装每个整数操作。  
  
 **若要打开检查算术上溢/下溢 C# 中**  
  
1.  在**解决方案资源管理器**，右键单击你的项目，然后选择**属性**。  
  
2.  选择**生成**选项卡，单击**高级**。  
  
3.  选择**检查算术上溢/下溢**单击**确定**。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.OverflowException?displayProperty=fullName>   
 [C# 运算符](/dotnet/csharp/language-reference/operators/index)   
 [Checked and Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)