---
title: "CA1502：避免过度复杂 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveComplexity"
  - "CA1502"
helpviewer_keywords: 
  - "CA1502"
  - "AvoidExcessiveComplexity"
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1502：避免过度复杂
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|类别|Microsoft.Maintainability|  
|是否重大更改|非重大更改|  
  
## 原因  
 某方法具有过度的圈复杂度。  
  
## 规则说明  
 “圈复杂度”通过方法来测量线性独立的路径的数量，该数量是由条件分支的数量和复杂度决定的。  较低的圈复杂度通常表示方法容易理解、测试和维护。  圈复杂度是通过方法的控件流图形计算的，计算公式如下：  
  
 圈复杂度 \= 边数 \- 节点数 \+ 1  
  
 其中节点表示逻辑分支点，边表示节点之间的直线。  
  
 当圈复杂度大于 25 时，该规则将报告冲突。  
  
 可以在[测量托管代码的复杂性和可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)这里详细了解代码度量，  
  
## 如何解决冲突  
 要解决与该规则的冲突，请重构该方法，以减少其圈复杂度。  
  
## 何时禁止显示警告  
 如果可以轻松地减少复杂度，并且很容易理解、测试和维护该方法，则可以安全地禁止显示与此规则有关的警告。  特别是当包含较大的 `switch`（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 `Select`）语句的方法是要排除的对象时。  与重构代码带来的可维护性好处相比，在以后的开发周期中破坏代码库的稳定性或者导致在以前发布的代码中的运行时行为发生意外变化的风险可能是得不偿失的。  
  
## 圈复杂度的计算方法  
 圈复杂度的计算方法是向以下项加 1：  
  
-   分支数（如 `if`、`while` 和 `do`）  
  
-   `switch` 中的 `case` 语句数。  
  
 下面的示例演示圈复杂度不断变化的方法。  
  
## 示例  
 **圈复杂度为 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## 示例  
 **圈复杂度为 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## 示例  
 **圈复杂度为 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## 示例  
 **圈复杂度为 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## 相关规则  
 [CA1501：避免过度继承](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## 请参阅  
 [测量托管代码的复杂性和可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)