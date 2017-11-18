---
title: "CA2147： 透明方法不得使用安全断言 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4893dbf799a964024fef59b7b0092b3066e8fdd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147：透明方法不得使用安全断言
|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 代码被标记为<xref:System.Security.SecurityTransparentAttribute>未被授予足够的权限进行断言。  
  
## <a name="rule-description"></a>规则说明  
 此规则分析所有方法和类型的程序集中的 100%透明或混合透明/关键，并标记的任何声明性或命令性用法<xref:System.Security.CodeAccessPermission.Assert%2A>。  
  
 在运行时，对任何调用<xref:System.Security.CodeAccessPermission.Assert%2A>从透明代码将导致<xref:System.InvalidOperationException>引发。 这可能发生在两个 100%透明程序集，以及在方法或类型被声明为透明，但包括声明性或命令性断言的混合透明/关键程序集。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 引入了一个名为功能*透明度*。 单个方法、 字段、 接口、 类和类型可以是透明的或关键。  
  
 透明代码不允许安全特权提升。 因此，授予或要求它的任何权限都会自动通过代码传递到调用方或主机应用程序域。 特权提升的示例包括 assert 语句、 Linkdemand、 SuppressUnmanagedCode，和`unsafe`代码。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要解决此问题，请标记的代码调用与该断言<xref:System.Security.SecurityCriticalAttribute>，或删除该断言。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不要禁止显示此规则的消息。  
  
## <a name="example"></a>示例  
 此代码将失败，如果`SecurityTestClass`是透明的当`Assert`方法抛出异常<xref:System.InvalidOperationException>。  
  
 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]  
  
## <a name="example"></a>示例  
 一种选择是到代码评审 SecurityTransparentMethod 方法在示例中，而且如果此方法被认为安全的提升，将标记 SecurityTransparentMethod 使用安全关键这种方式要求详细、 完整和错误可用的安全必须在上以及在所断言的方法中发生任何调用的超时值的方法执行审核：  
  
 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]  
  
 另一个选项是从代码中，删除该断言，让任何后续的文件 I/O 权限需求流超出 SecurityTransparentMethod 给调用方。 这使安全检查。 在这种情况下，通常需要无任何安全审核，因为权限要求将流到调用方和/或应用程序域。 通过安全策略、 宿主环境中，并相应地代码源权限授予密切控制权限需求。  
  
## <a name="see-also"></a>另请参阅  
 [安全警告](../code-quality/security-warnings.md)