---
title: "CA2213： 应释放可释放字段 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 77cd32f97e3798362371fc21f8b38c14ce22c7fb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213：应释放可释放的字段
|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 实现一种<xref:System.IDisposable?displayProperty=fullName>声明还实现的类型的字段<xref:System.IDisposable>。 <xref:System.IDisposable.Dispose%2A>的字段的方法不由调用<xref:System.IDisposable.Dispose%2A>声明类型的方法。  
  
## <a name="rule-description"></a>规则说明  
 一种类型负责释放所有其非托管资源;这通过实现实现<xref:System.IDisposable>。 此规则检查以确定是否可释放类型`T`声明字段`F`，它是可释放类型的实例`FT`。 每个字段`F`，规则将尝试查找调用`FT.Dispose`。 规则将搜索由调用的方法`T.Dispose`，和一个级别较低 (由调用的方法调用的方法`FT.Dispose`)。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，调用<xref:System.IDisposable.Dispose%2A>上实现的类型的字段<xref:System.IDisposable>如果你将负责分配和释放的非托管的资源包含的字段。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果不能负责为释放资源包含字段，或者如果调用<xref:System.IDisposable.Dispose%2A>发生时的更深入地调用级别比规则检查。  
  
## <a name="example"></a>示例  
 下面的示例演示一种类型`TypeA`实现<xref:System.IDisposable>(`FT`上文中讨论)。  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## <a name="example"></a>示例  
 下面的示例演示一种类型`TypeB`了违反此规则通过声明一个字段`aFieldOfADisposableType`(`F`前面讨论中) 为可释放类型 (`TypeA`) 而不调用<xref:System.IDisposable.Dispose%2A>字段。 `TypeB`对应于`T`中前面的讨论。  
  
 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.IDisposable?displayProperty=fullName>   
 [释放模式](/dotnet/standard/design-guidelines/dispose-pattern)