---
title: "CA1502： 避免过度复杂 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c45ca232b555af1441502586a38c80f43c41edc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502：避免过度复杂
|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|类别|Microsoft.Maintainability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 一种方法具有过多的圈复杂度。  
  
## <a name="rule-description"></a>规则说明  
 *圈复杂度*测量线性独立的路径的通过方法由数量和复杂度条件分支的数量。 低圈复杂度通常表示很容易理解、 测试和维护的方法。 圈复杂度计算出的方法的控件流图形，并给出，如下所示：  
  
 圈复杂度 = 边缘的节点数 + 1 的数  
  
 其中一个节点表示逻辑分支点，边缘表示节点之间的直线。  
  
 当圈复杂度超过 25 时，规则将报告冲突。  
  
 你可以了解有关在代码度量[测量复杂性和托管代码可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)，  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，重构的方法，以减少其圈复杂度。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果不能轻松地降低的复杂程度，并且很容易理解、 测试和维护方法。 具体而言，一个方法，包含大量`switch`(`Select`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 语句可用于排除。 破坏基本后期开发周期或引入在以前发布的代码中的运行时行为中发生意外的更改中可能会得不偿失可维护性重构代码的代码的风险。  
  
## <a name="how-cyclomatic-complexity-is-calculated"></a>如何计算圈复杂度  
 圈复杂度的计算通过将 1 添加到以下：  
  
-   分支的数目 (如`if`， `while`，和`do`)  
  
-   数`case`中的语句`switch`  
  
 下面的示例演示圈复杂度不断变化的方法。  
  
## <a name="example"></a>示例  
 **1 的圈复杂度**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## <a name="example"></a>示例  
 **2 的圈复杂度**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## <a name="example"></a>示例  
 **3 的圈复杂度**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## <a name="example"></a>示例  
 **8 的圈复杂度**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1501：避免过度继承](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## <a name="see-also"></a>另请参阅  
 [测量托管代码的复杂性和可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)