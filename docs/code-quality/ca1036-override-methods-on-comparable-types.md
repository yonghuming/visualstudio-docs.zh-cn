---
title: "CA1036： 重写可比较类型的方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d07e63363542a9bf5a1dd756026183349659abe1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036：重写可比较类型中的方法
|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 公共或受保护类型实现<xref:System.IComparable?displayProperty=fullName>接口，并在不重写<xref:System.Object.Equals%2A?displayProperty=fullName>也不重载表示相等、 不等、 小于或大于的语言特定运算符。 如果该类型继承仅接口的实现，该规则不会报告发生的冲突。  
  
## <a name="rule-description"></a>规则说明  
 定义自定义排序顺序的类型实现<xref:System.IComparable>接口。 <xref:System.IComparable.CompareTo%2A>方法返回一个整数值，该值指示两个类型的正确的排序顺序。 此规则标识设置的排序顺序; 的类型这意味着，相等、 不等的普通含义小于且大于不适用于。 提供的实现时<xref:System.IComparable>，通常必须还重写<xref:System.Object.Equals%2A>从而使其返回值与相一致<xref:System.IComparable.CompareTo%2A>。 如果你重写<xref:System.Object.Equals%2A>和在编码中支持的语言中运算符重载，你还应提供与相一致的运算符<xref:System.Object.Equals%2A>。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，重写<xref:System.Object.Equals%2A>。 如果您的编程语言支持运算符重载，提供以下运算符：  
  
-   op_Equality  
  
-   op_Inequality  
  
-   op_LessThan  
  
-   op_GreaterThan  
  
 在 C# 中，用于表示这些运算符的令牌如下所示: = =、 ！ =、 \<，和 >。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，当因缺少运算符引起冲突和您的编程语言不支持运算符重载，这与 Visual Basic.NET 情况相同。 还有安全地禁止显示此规则的警告，而非 op_Equality 如果你确定实现运算符没有意义应用程序上下文中激发上相等运算符时。 但是，你应始终通过 op_Equality 与 = = 运算符，如果重写 Object.Equals。  
  
## <a name="example"></a>示例  
 下面的示例包含的类型正确实现<xref:System.IComparable>。 标识满足与相关的各种规则的方法的代码注释<xref:System.Object.Equals%2A>和<xref:System.IComparable>接口。  
  
 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## <a name="example"></a>示例  
 下面的应用程序测试的行为<xref:System.IComparable>前面所示的实现。  
  
 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [相等运算符](/dotnet/standard/design-guidelines/equality-operators)