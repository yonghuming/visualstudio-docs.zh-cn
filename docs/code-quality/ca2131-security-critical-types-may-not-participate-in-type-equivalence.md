---
title: "CA2131： 安全关键类型不能参与类型等效性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 90789a7a632084d157f94f72deb1c06370223056
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131：安全关键类型不能参与类型等效
|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 某个类型参与类型等效性和该类型本身，或用标记的成员或字段的类型，<xref:System.Security.SecurityCriticalAttribute>属性。  
  
## <a name="rule-description"></a>规则说明  
 对于任何关键的类型或包含参与类型等效的关键方法或字段的类型，将引发此规则。 当 CLR 检测到这样的类型时，它无法加载其与<xref:System.TypeLoadException>在运行时。 通常，仅在用户手动实现类型等效而不是通过依赖 tlbimp 和编译器进行类型等效时，才会触发此规则。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，删除 SecurityCritical 属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示一个接口、 方法和一个字段，它将导致触发此规则。  
  
 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 [安全透明的代码，级别 2](http://msdn.microsoft.com/Library/4d05610a-0da6-4f08-acea-d54c9d6143c0)