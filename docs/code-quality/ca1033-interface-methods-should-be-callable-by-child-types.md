---
title: "CA1033： 接口方法应可由子类型调用 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4694e1dbcbcf541b502edbe5f2520229ee33f4a6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033：接口方法应可由子类型调用
|||  
|-|-|  
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|  
|CheckId|CA1033|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 未密封的外部可见类型提供了显式实现公共接口的方法，但没有提供具有相同名称的其他外部可见方法。  
  
## <a name="rule-description"></a>规则说明  
 请考虑显式实现公共接口方法的基类型。 派生自基类型的类型可以访问继承的接口方法，只能通过对当前实例的引用 (`this` C# 中)，被强制转换为接口。 如果派生的类型重新实现 （显式） 继承的接口方法，可以不再访问的基实现。 通过当前的实例引用的调用将调用派生的实现;这将导致递归和最终堆栈溢出。  
  
 此规则不会报告的显式实现的违反<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>在外部可见时`Close()`或`System.IDisposable.Dispose(Boolean)`提供方法。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，实现公开相同的功能且可见到派生类型的新方法，或者更改为非显式实现。 如果可接受一项重大更改，一种替代方法是使密封的类型。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果外部可见方法提供了具有相同的功能，但不同于显式实现的方法的名称。  
  
## <a name="example"></a>示例  
 下面的示例演示一种类型， `ViolatingBase`，了违反规则和类型， `FixedBase`，，显示了冲突的修补程序。  
  
 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 [接口](/dotnet/csharp/programming-guide/interfaces/index)