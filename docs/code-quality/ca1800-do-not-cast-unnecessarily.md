---
title: "Ca1800： 避免进行不强制不必要地转换 |Microsoft 文档"
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 1d59983639284fb8a6134a73ea58e09c6d49b183
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800：避免进行不必要的强制转换
|||  
|-|-|  
|TypeName|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
一种方法之一其参数或局部变量上执行重复强制转换。

用于此规则的完整分析，必须使用调试信息生成测试的程序集和关联的程序数据库 (.pdb) 文件必须可用。  
  
## <a name="rule-description"></a>规则说明  
重复强制转换会降低性能，特别是在精简的迭代语句中执行强制转换时。 对于显式重复强制转换操作，该强制转换的结果存储在本地变量和使用本地变量，而不是重复的转换运算。  
  
如果 C#`is`运算符用于测试是否强制转换会成功之前执行实际的强制转换，则测试的结果，请考虑`as`运算符相反。 这提供相同的功能，而无需执行的隐式强制转换操作`is`运算符。 或者，在 C# 7.0 及更高版本，使用`is`运算符具有[模式匹配](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is)检查类型转换，并将该类型的变量的表达式强制转换在一个步骤。
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，修改要强制转换操作的数量降到最低的方法实现。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果性能并不是问题，它是安全地禁止显示此规则的警告，或者完全，忽略此规则。  
  
## <a name="examples"></a>示例  
 下面的示例演示使用 C# 中违反规则的方法`is`运算符。 第二种方法通过替换来满足该规则`is`运算符具有针对的结果的测试`as`运算符，减少每个迭代两个到一个强制转换操作的数目。 第三种方法还使用满足该规则`is`与[模式匹配](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is)创建所需的类型的变量，如果类型转换会成功。
  
 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  

 下面的示例演示一种方法， `start_Click`，具有多个重复显式强制转换，这违反了该规则和方法， `reset_Click`，以及通过在本地变量中存储该强制转换满足该规则。  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## <a name="see-also"></a>另请参阅  
[作为 （C# 参考）](/dotnet/csharp/language-reference/keywords/as)   
[是 （C# 参考）](/dotnet/csharp/language-reference/keywords/is)