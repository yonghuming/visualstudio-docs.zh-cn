---
title: "CA1810： 引用类型的静态字段以内联方式初始化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 113d5206d2b4827902cf83827efd5b8738387755
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810：以内联方式初始化引用类型的静态字段
|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 引用类型声明显式静态构造函数。  
  
## <a name="rule-description"></a>规则说明  
 当一个类型声明显式静态构造函数时，实时 (JIT) 编译器会向该类型的每个静态方法和实例构造函数中添加一项检查，以确保之前已调用该静态构造函数。 访问任何静态成员时，或创建类型的实例时，都会触发静态初始化。 但是，如果声明类型的变量，但不是使用它，可以是重要信息： 如果在初始化更改全局状态的则不会触发静态初始化。  
  
 在所有静态数据都初始化的内联且未声明了显式静态构造函数，Microsoft 中间语言 (MSIL) 编译器将添加`beforefieldinit`标志和隐式静态构造函数，其初始化静态数据，甚至到 MSIL 类型定义。 当 JIT 编译器遇到`beforefieldinit`标志，大多数情况下不会添加静态构造函数检查。 静态初始化保证访问任何静态字段前，但不是在静态方法或实例构造函数进行调用之前在某个时间发生。 请注意静态初始化可以在任何时间类型的变量声明后发生。  
  
 静态构造函数检查会降低性能。 通常一个静态构造函数是仅用于初始化静态字段，你必须仅确保静态初始化的情况下发生之前的静态字段的第一个访问权限。 `beforefieldinit`行为是适用于这些和大多数其他类型。 不适合当时它才静态初始化影响全局状态且下列其中一项为 true:  
  
-   对全局状态的影响很高，如果不使用该类型不需要。  
  
-   无需访问该类型的任何静态字段，可以访问全局状态的副作用。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 要修复与该规则的冲突，请在声明它时初始化所有静态数据并移除静态构造函数。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果性能并不是问题;或如果引起静态初始化的全局状态更改非常昂贵，或必须保证发生之前调用类型的静态方法或创建类型的实例。  
  
## <a name="example"></a>示例  
 下面的示例演示一种类型， `StaticConstructor`，了违反规则和类型， `NoStaticConstructor`，静态构造函数替换内联初始化，以满足该规则。  
  
 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]  
  
 请注意添加`beforefieldinit`标志的 MSIL 定义`NoStaticConstructor`类。  
  
 **.class 公共自动 ansi StaticConstructor**  
 **扩展 [mscorlib]System.Object**  
**{**  
**} / / 结束类 StaticConstructor 的**  
**.class 公共自动 ansi beforefieldinit NoStaticConstructor**  
 **扩展 [mscorlib]System.Object**  
**{**  
**} / / 结束类 NoStaticConstructor 的**   
## <a name="related-rules"></a>相关的规则  
 [CA2207：以内联方式初始化值类型的静态字段](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)