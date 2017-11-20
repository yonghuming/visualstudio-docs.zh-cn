---
title: "CA2107： 检查 deny 权限和允许仅使用情况 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fb802e0d97d265c01540ca10ffe8d0dcf9b273cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107：检查 deny 权限和 permit only 权限的使用情况
|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 方法包含指定的 PermitOnly 或拒绝安全操作的安全检查。  
  
## <a name="rule-description"></a>规则说明  
 [使用 PermitOnly 方法](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649)和<xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>应仅通过具有高级的知识的人员使用安全操作的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]安全。 应当对使用这些安全操作的代码进行安全检查。  
  
 拒绝更改对安全请求响应中发生堆栈审核的默认行为。 它允许你指定必须未在拒绝的方法，无论调用堆栈中的调用方的实际权限的持续时间内授予的权限。 如果堆栈审核检测到由 Deny，保护的方法，并且如果要求的权限包含在被拒绝的权限，则堆栈审核将失败。 PermitOnly 也会更改堆栈审核的默认行为。 它允许代码来指定无论调用方的权限，可授予的权限。 如果堆栈审核检测到 PermitOnly，受保护的方法，且要求的权限不包含由 PermitOnly 指定权限中，堆栈审核失败。  
  
 依赖于这些操作的代码应仔细评估对安全漏洞，由于其用途有限和微妙的行为。 考虑以下情况：  
  
-   [链接需求](/dotnet/framework/misc/link-demands)的 Deny 或 PermitOnly 不会影响。  
  
-   如果拒绝或 PermitOnly 发生作为导致堆栈审核的需求相同的堆栈帧中，安全操作将产生任何影响。  
  
-   通常可以采用多种方式指定用于构造基于路径的权限的值。 拒绝对一种形式的路径访问并不影响到所有窗体的访问。 例如，如果文件共享\\\Server\Share 映射到网络驱动器 x:，以拒绝访问的文件在共享上，你必须拒绝\\\Server\Share\File、 X:\File 和访问文件的每个其他路径。  
  
-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>可以在达到拒绝或 PermitOnly 之前终止堆栈审核。  
  
-   如果拒绝都没有任何效果，也就是说，当调用方具有的权限被拒绝，阻止调用方可以访问受保护的资源直接，绕过拒绝。 同样，如果调用方没有被拒绝的权限，堆栈审核将失败即使不存在 Deny。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 任何使用这些安全操作将导致冲突。 若要解决冲突，不要使用这些安全操作。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 只有在完成安全检查后，禁止显示此规则的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示拒绝一些限制。  
  
 以下库包含具有相同保护它们的安全需求除外的两种方法的类。  
  
 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
## <a name="example"></a>示例  
 下面的应用程序从库中演示的拒绝对受保护的方法的影响。  
  
 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]  
  
 本示例生成以下输出。  
  
 **随需应变： 调用方的拒绝不起按需使用断言的权限。**  
**LinkDemand： 调用方的拒绝不起 LinkDemand 使用断言的权限。**  
**LinkDemand： 调用方的拒绝不起使用 LinkDemand 保护代码。**  
**LinkDemand： 此拒绝不起使用 LinkDemand 保护代码。**   
## <a name="see-also"></a>另请参阅  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [安全编码准则](/dotnet/standard/security/secure-coding-guidelines)   
 [重写安全检查](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [使用 PermitOnly 方法](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649)