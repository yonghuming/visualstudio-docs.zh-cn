---
title: "CA2214： 不要在构造函数中调用可重写方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbe640ac82c159b39721ddac27b9d65926c60647
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214：不要在构造函数中调用可重写的方法
|||  
|-|-|  
|TypeName|DoNotCallOverridableMethodsInConstructors|  
|CheckId|CA2214|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 未密封的类型的构造函数调用其类中定义的虚方法。  
  
## <a name="rule-description"></a>规则说明  
 当调用的虚方法时，直到运行时未选择的实际类型所执行方法。 时构造函数调用虚方法，则可能不具有执行调用方法的实例的构造函数。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请勿调用该类型从该类型的构造函数内的虚方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 构造函数应重新设计，以消除对虚拟方法的调用。  
  
## <a name="example"></a>示例  
 下面的示例演示了违反此规则的效果。 测试应用程序创建的实例`DerivedType`，这将导致其基本类 (`BadlyConstructedType`) 构造函数来执行。 `BadlyConstructedType`构造函数不正确地调用虚方法`DoSomething`。 如输出所示，`DerivedType.DoSomething()`执行，并且因此之前是`DerivedType`的构造函数执行。  
  
 [!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]  
  
 本示例生成以下输出。  
  
 **调用基 ctor。**  
**调用派生的 DoSomething-初始化？不**  
**调用派生 ctor。**