---
title: "CA1802： 在适当使用文本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 66ee20e099de0206664390623b7a50c5fec723a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802：在合适的位置使用文本
|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 字段声明`static`和`readonly`(`Shared`和`ReadOnly`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])，并使用一个值，在编译时是可初始化。  
  
## <a name="rule-description"></a>规则说明  
 值`static``readonly`时调用的声明类型的静态构造函数，在运行时将计算字段。 如果`static``readonly`时，它声明和静态构造函数未显式声明，则编译器可以发射静态构造函数来初始化该字段，字段进行初始化。  
  
 值`const`在编译时计算字段并将其存储在元数据，从而增加运行时性能相比到`static``readonly`字段。  
  
 由于分配给目标字段的值是可在编译时，将声明更改为`const`字段，以便在编译时而不是在运行时计算的值。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请替换`static`和`readonly`修饰符用于`const`修饰符。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果性能不是问题的，它是问题的安全地禁止显示此规则的警告，或者禁用规则。  
  
## <a name="example"></a>示例  
 下面的示例演示一种类型， `UseReadOnly`，了违反规则和类型， `UseConstant`，满足该规则。  
  
 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]