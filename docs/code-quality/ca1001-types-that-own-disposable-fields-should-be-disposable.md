---
title: "Ca1001： 具有可释放字段的类型应该是可释放 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 30609be8b70f65cb48478c6d6d2c0f3b6d89a029
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001：具有可释放字段的类型应该是可释放的
|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|类别|Microsoft.Design|  
|是否重大更改|无间断-如果类型不是程序集外部可见。<br /><br /> 中断性-如果该类型是在程序集外可见。|  
  
## <a name="cause"></a>原因  
 一个类声明并实现一个实例字段，它是<xref:System.IDisposable?displayProperty=fullName>类型和类未实现<xref:System.IDisposable>。  
  
## <a name="rule-description"></a>规则说明  
 类实现<xref:System.IDisposable>接口来释放它拥有的非托管资源。 是的实例字段<xref:System.IDisposable>类型指示该字段拥有非托管的资源。 声明的类<xref:System.IDisposable>字段间接拥有非托管的资源，并且应该实现<xref:System.IDisposable>接口。 如果类不直接拥有任何非托管的资源，它不应实现终结器。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，实现<xref:System.IDisposable>和从<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>方法调用<xref:System.IDisposable.Dispose%2A>字段方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示与该规则冲突的类和类通过实现满足该规则<xref:System.IDisposable>。 类未实现终结器，因为类不直接拥有任何非托管的资源。  
  
 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2213：应释放可释放的字段](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216：可释放类型应声明终结器](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215：Dispose 方法应调用基类 Dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049：拥有本机资源的类型应可释放](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)