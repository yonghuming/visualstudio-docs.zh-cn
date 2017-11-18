---
title: "CA1052： 应密封静态容器类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: deb02958ac89c350c4dc616b68693ee41b3019f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052：应密封静态容器类型
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护类型仅包含静态成员，并且不声明与[密封](/dotnet/csharp/language-reference/keywords/sealed)([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) 修饰符。  
  
## <a name="rule-description"></a>规则说明  
 此规则假定只包含静态成员的类型未设计为被继承，因为类型没有提供可以重写派生类型中的任何功能。 未计划继承的类型应该用 `sealed` 修饰符进行标记，以便禁止其作为基类型使用。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将类型标记为`sealed`。 如果你正面向[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]2.0 或更高版本，更好的方法是将类型标记为`static`。 在这种方式，你应避免出现声明一个私有构造函数，以防止从正在创建的类。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 禁止显示此规则的警告，仅当类型都旨在被继承。 缺少`sealed`修饰符意味着类型非常有用的基类型。  
  
## <a name="example-of-a-violation"></a>冲突的示例  
  
### <a name="description"></a>描述  
 下面的示例演示与该规则冲突的类型。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>修复静态修饰符  
  
### <a name="description"></a>描述  
 下面的示例演示如何修复此规则的冲突错误标记具有的类型`static`修饰符。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1053：静态容器类型不应具有构造函数](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
