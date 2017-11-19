---
title: "CA2123： 重写链接请求应与基相同 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e39d278588d8fbce5bc9a7ee77141a56341e8f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123：重写的链接请求应与基相同
|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护方法的公共类型中重写一个方法或实现一个接口，并且不具有同一[链接需求](/dotnet/framework/misc/link-demands)与该接口或虚方法。  
  
## <a name="rule-description"></a>规则说明  
 该规则将一个方法与其基方法（该基方法为另一个类型中的接口或虚方法）相匹配，然后比较两者的链接请求。 如果在方法或基方法具有链接要求和另一个不会报告冲突。  
  
 如果违反了此规则，则恶意调用方只需调用不安全的方法，可以跳过链接要求。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，应用到重写方法或实现相同的链接要求。 如果这是不可能，将标记具有完全的请求的方法或完全删除特性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示各种违反此规则。  
  
 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 [安全编码准则](/dotnet/standard/security/secure-coding-guidelines)   
 [链接需求](/dotnet/framework/misc/link-demands)