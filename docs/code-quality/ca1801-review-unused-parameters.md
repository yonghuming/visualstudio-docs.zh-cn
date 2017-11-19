---
title: "CA1801： 检查未使用的参数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1bb8c38d1436ca687664f92bfe0ba6db1ccf68ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1801-review-unused-parameters"></a>CA1801：检查未使用的参数
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改-如果成员不是程序集，而不考虑所做的更改外部可见。<br /><br /> 非重大更改-如果你更改要使用其主体中的参数的成员。<br /><br /> 中断性-如果删除参数，并且它是程序集外部可见。|  
  
## <a name="cause"></a>原因  
 方法签名包含一个没有在方法体中使用的参数。 此规则将不检查以下方法：  
  
-   引用的委托的方法。  
  
-   作为事件处理程序使用的方法。  
  
-   使用方法声明`abstract`(`MustOverride`在 Visual Basic 中) 修饰符。  
  
-   使用方法声明`virtual`(`Overridable`在 Visual Basic 中) 修饰符。  
  
-   使用方法声明`override`(`Overrides`在 Visual Basic 中) 修饰符。  
  
-   使用方法声明`extern`(`Declare`在 Visual Basic 中的语句) 修饰符。  
  
## <a name="rule-description"></a>规则说明  
 检查在不使用的方法体中以确保不存在环绕故障对其进行访问的非虚拟方法中的参数。 未使用的参数会产生维护和性能成本。  
  
 此规则的冲突有时，可能实现中的 bug 的方法。 例如，该参数应该具有已使用的方法体中。 如果该参数必须存在由于向后兼容性，禁止显示此规则的警告。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，删除未使用的参数 （一项重大更改），或在方法体 （非重大更改） 中使用参数。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则，以前发布的解决方法将一项重大更改的代码的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示两种方法。 一种方法违反了规则和其他方法满足该规则。  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1811：避免使用未调用的私有代码](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812：避免未实例化的内部类](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804：移除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md)