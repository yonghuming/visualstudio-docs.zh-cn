---
title: "CA1026： 默认参数不应使用 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d7a850c959787282cdf6f9d24b392ef4684b7dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026：不应使用默认参数
|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|CheckId|CA1026|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 外部可见类型包含外部可见方法使用的默认参数。  
  
## <a name="rule-description"></a>规则说明  
 使用默认参数的方法允许在公共语言规范 (CLS);但是，CLS 允许编译器忽略为这些参数分配的值。 为忽略默认参数值的编译器编写的代码必须显式提供每个默认参数的自变量。 若要维护需要跨编程语言的行为，应使用提供默认参数的方法重载替换使用默认参数的方法。  
  
 在访问托管的代码时，编译器将默认参数的值的托管扩展忽略 c + +。 Visual Basic 编译器支持具有默认参数使用方法的[可选](/dotnet/visual-basic/language-reference/modifiers/optional)关键字。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将使用提供默认参数的方法重载使用默认参数的方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示使用默认参数的方法并提供等效的功能的重载的方法。  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1025：用形参数组替换重复的实参](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## <a name="see-also"></a>另请参阅  
 [语言独立性和与语言无关的组件](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)