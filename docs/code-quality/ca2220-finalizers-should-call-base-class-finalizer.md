---
title: "CA2220： 终结器应调用基类的终结器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa5ed3329d4168a0781243a4faf021de3488e77c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220：终结器应调用基类的终结器
|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 重写的类型<xref:System.Object.Finalize%2A?displayProperty=fullName>不调用<xref:System.Object.Finalize%2A>其基类中的方法。  
  
## <a name="rule-description"></a>规则说明  
 终止必须通过继承层次结构传播。 若要确保这一点，类型必须调用其基类<xref:System.Object.Finalize%2A>方法从其自身<xref:System.Object.Finalize%2A>方法。 C# 编译器会自动添加对基类的终结器的调用。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，调用基类型的<xref:System.Object.Finalize%2A>方法从你<xref:System.Object.Finalize%2A>方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 面向公共语言运行时的某些编译器插入的 Microsoft 中间语言 (MSIL) 的基类型的终结器调用。 如果报告此规则的警告，你的编译器不会插入调用，并且必须将其添加到你的代码。  
  
## <a name="example"></a>示例  
 下面的 Visual Basic 示例演示一种类型`TypeB`正确调用<xref:System.Object.Finalize%2A>其基类中的方法。  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## <a name="see-also"></a>另请参阅  
 [释放模式](/dotnet/standard/design-guidelines/dispose-pattern)