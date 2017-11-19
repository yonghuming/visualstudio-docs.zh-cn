---
title: "CA2222： 不要递减继承的成员的可见性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 520882b8d1b24cc7bc346ae185de8f186e4fa163
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222：不要递减继承成员的可见性
|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 未密封的类型中的私有方法有一个等同于基类型中声明的公共方法的签名。 私有方法不是最终的。  
  
## <a name="rule-description"></a>规则说明  
 不能更改所继承成员的访问修饰符。 将继承的成员更改为私有成员不能防止调用方访问该方法的基类实现。 如果设为私有成员，并且该类型是未密封，则继承类型可以调用继承层次结构中的方法的最后一个公共实现。 如果必须更改的访问修饰符，则应最终标记该方法或其类型应为密封的以防止方法被重写。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，更改为非私有的访问权限。 或者，如果您的编程语言支持它，你可以将此方法最终。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示了违反此规则的类型。  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]