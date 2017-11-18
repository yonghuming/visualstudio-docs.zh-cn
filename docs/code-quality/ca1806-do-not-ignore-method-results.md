---
title: "CA1806： 不要忽略方法结果 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 58da9a40f8cbbf8a506feb35dcba8a8e9f405899
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806：不要忽略方法结果
|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 有几个可能的原因，此警告：  
  
-   一个新的对象已创建，但从未使用过。  
  
-   创建并返回一个新字符串的方法称为，永远不会使用新的字符串。  
  
-   COM 或 P/Invoke 方法，返回从未使用过的 HRESULT 或错误代码。 规则说明  
  
 不必要的对象创建和未使用的对象的关联的垃圾回收会降低性能。  
  
 字符串是不可变，并如 String.ToUpper 方法返回的字符串，而非修改在调用方法中字符串的实例的新实例。  
  
 忽略 HRESULT 或错误代码可能会导致意外行为在错误条件或资源不足的情况。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 如果方法 A 创建从未使用过的 B 对象的新实例，将实例作为参数传递到另一种方法，或将实例分配给一个变量。 如果创建对象是不必要的则删除它。-或-  
  
 如果方法 A 调用 B，但未使用新 B 该方法返回的字符串实例。 将实例作为参数传递到另一种方法，将实例分配给一个变量。 或者，如果它是不必要移除此调用。  
  
 - 或 -  
  
 如果方法 A 调用 B，但未使用的 HRESULT 或错误代码，该方法返回。 在条件语句中使用的结果、 将结果赋给一个变量，或将其作为自变量传递到另一种方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 除非创建对象的操作有特定的用途不禁止显示此规则的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示将忽略调用 String.Trim 的结果的类。  
  
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例修复 String.Trim 的结果赋回给调用了该变量的前面的冲突。  
  
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例演示不使用它创建的对象的方法。  
  
> [!NOTE]
>  无法在 Visual Basic 中重现此冲突。  

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]   
  
## <a name="example"></a>示例  
 下面的示例通过删除不必要创建对象修复前面的冲突。  

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)] 

<!-- Examples don't exist for the below... -->
<!--
## Example  
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.  
  
## Example  
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.  
-->