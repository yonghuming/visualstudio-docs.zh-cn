---
title: "CA2119： 密封满足私有接口的方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f05b59ffc48b072d1a94ddfd405072d9663e6257
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119：密封满足私有接口的方法
|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 可继承的公共类型提供的可重写方法实现`internal`(`Friend`在 Visual Basic 中) 接口。  
  
## <a name="rule-description"></a>规则说明  
 接口方法具有公共可访问性，不能更改实现的类型。 内部接口创建不是要定义的接口的程序集外部实现的协定。 实现方法的内部接口使用的公共类型`virtual`(`Overridable`在 Visual Basic 中) 修饰符允许由程序集外部的派生类型中重写该方法。 如果定义的程序集中的第二个类型调用方法，并需要一个仅限内部使用的协定，行为可能受到影响时，而执行的重写的方法中的外部程序集。 这会产生安全漏洞。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，防止方法被重写程序集外部的通过使用以下项之一：  
  
-   使声明类型`sealed`(`NotInheritable`在 Visual Basic 中)。  
  
-   更改的声明类型的可访问性`internal`(`Friend`在 Visual Basic 中)。  
  
-   从声明的类型中删除所有的公共构造函数。  
  
-   实现方法，而无需使用`virtual`修饰符。  
  
-   显式实现的方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此警告规则，认真检查后没有安全存在问题的情况，可能是如果在程序集外重写该方法利用。  
  
## <a name="example"></a>示例  
 下面的示例演示一种类型， `BaseImplementation`，违反此规则。  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## <a name="example"></a>示例  
 下面的示例利用前面的示例的虚方法实现。  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## <a name="see-also"></a>另请参阅  
 [接口](/dotnet/csharp/programming-guide/interfaces/index)   
 [接口](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)