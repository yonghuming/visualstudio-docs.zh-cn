---
title: "CA1019： 定义特性自变量的访问器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f04a49c8c68fcc597ecd98471b46932d467b365
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019：定义特性参数的访问器
|||  
|-|-|  
|TypeName|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 在其构造函数，属性定义没有相应的属性的自变量。  
  
## <a name="rule-description"></a>规则说明  
 特性可以定义强制实参，在对目标应用该特性时必须指定这些实参。 这些实参也称为位置实参，因为它们将作为位置形参提供给特性构造函数。 对于每一个强制变量，特性还必须提供一个相应的只读属性，以便可以在执行时检索该变量的值。 此规则检查每个构造函数参数，你已经定义对应的属性。  
  
 特性还可以定义可选实参，可选实参也称为命名实参。 这些变量按名称提供给特性构造函数，并且必须具有相应的读/写属性。  
  
 对于必需和可选自变量时，相应的属性和构造函数参数应使用相同的名称但不同大小写。 属性使用 Pascal 大小写和参数使用 camel 大小写。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，添加一个不具有每个构造函数参数的只读属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果你不想要无法检索该项目的必需自变量的值，禁止显示此规则的警告。  
  
## <a name="custom-attributes-example"></a>自定义特性的示例  
  
### <a name="description"></a>描述  
 下面的示例演示两个特性所定义的必需的 （位置） 参数。 未正确定义该属性的第一个实现。 第二种实现是正确的。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## <a name="positional-and-named-arguments"></a>位置和命名自变量  
  
### <a name="description"></a>描述  
 位置和命名自变量可以让你的库哪些参数是必需的属性，哪些参数是可选的使用者清楚。  
  
 下面的示例演示具有位置和命名自变量的属性的实现。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### <a name="comments"></a>注释  
 下面的示例演示如何将自定义特性应用于两个属性。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1813：避免使用未密封的特性](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>另请参阅  
 [特性](/dotnet/standard/design-guidelines/attributes)