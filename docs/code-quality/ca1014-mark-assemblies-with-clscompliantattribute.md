---
title: "CA1014： 将程序集用 CLSCompliantAttribute 标记 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a870721f0bf7192b417d2105635c663fb69713c7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014：用 CLSCompliantAttribute 标记程序集
|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 程序集没有<xref:System.CLSCompliantAttribute?displayProperty=fullName>特性应用于它。  
  
## <a name="rule-description"></a>规则说明  
 公共语言规范 (CLS) 定义了程序集在跨编程语言使用时必须符合的命名限制、数据类型和规则。 合理的设计指出程序的所有程序集将显式指示 CLS 遵从性与<xref:System.CLSCompliantAttribute>。 如果该属性不存在的程序集，程序集即不合规。  
  
 它有可能包含类型或类型成员不符合 cls 的程序集。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将添加到程序集的属性。 而不是标记为不符合要求的整个程序集，你应确定哪些类型或类型成员不符合并将这些元素在这种标记。 如果可能，应为不符合的成员提供符合 cls 的替代方法，以便尽可能多的用户可以访问您的程序集的所有功能。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 如果你不想要符合的程序集，应用该特性并将其值设置为`false`。  
  
## <a name="example"></a>示例  
 下面的示例演示具有的程序集<xref:System.CLSCompliantAttribute?displayProperty=fullName>应用声明它符合 CLS 的特性。  
  
 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [语言独立性和与语言无关的组件](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)