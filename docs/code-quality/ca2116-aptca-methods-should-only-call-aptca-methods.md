---
title: "CA2116: APTCA 方法应只调用 APTCA 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 92c6a91cffc3ce388a3dfb9000b9f432672018f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116：APTCA 方法应只调用 APTCA 方法
|||  
|-|-|  
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|  
|CheckId|CA2116|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 中包含的程序集的方法<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>特性的程序集中不具有属性的调用的方法。  
  
## <a name="rule-description"></a>规则说明  
 默认情况下，具有强名称的程序集的公共或受保护方法隐式受[链接需求](/dotnet/framework/misc/link-demands)完全信任; 只能完全受信任调用方可以访问的强名称程序集。 强名称的程序集标记为<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 特性未启用此保护。 该属性禁用此链接要求，使该程序集不具有完全信任，如执行从 intranet 或 Internet 的代码的调用方可以访问。  
  
 APTCA 特性在完全受信任的程序集后，该程序集执行代码中不允许部分受信任的调用方的另一个程序集，则可能产生安全漏洞。 如果两个方法`M1`和`M2`满足以下条件，则恶意调用方可以使用该方法`M1`绕过的隐式的完全信任链接要求保护`M2`:  
  
-   `M1`在完全受信任的程序集具有 APTCA 特性中声明的公共方法。  
  
-   `M1`调用方法`M2`外部`M1`的程序集。  
  
-   `M2`程序集不具有 APTCA 特性，并且，因此，不应执行的操作或代表部分受信任的调用方。  
  
 部分受信任的调用方`X`可以调用方法`M1`，从而导致`M1`调用`M2`。 因为`M2`没有 APTCA 特性，其直接调用方 (`M1`) 必须满足针对完全信任; 的链接要求`M1`具有完全信任权限并且因此满足此检查。 安全风险是因为`X`不参与满足此链接要求保护`M2`通过不受信任的调用方。 因此，用 APTCA 特性方法不得调用不具有属性的方法。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 如果 APCTA 特性是必需的则使用要求来保护调入完全信任程序集的方法。 确切的权限，您需将取决于你的方法所公开的功能。 如果可能，保护要求完全信任以确保基础功能不会公开给部分受信任的调用方提供的方法。 如果这是不可能，请选择有效地保护已公开的功能的权限集。 有关要求的详细信息，请参阅[需求](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 若要安全地禁止显示此规则的警告，必须确保由你的方法公开的功能不会直接或间接允许调用方访问敏感信息、 操作或可以以的破坏性方式使用的资源。  
  
## <a name="example"></a>示例  
 下面的示例使用两个程序集和测试应用程序演示此规则检测到的安全漏洞。 第一个程序集不具有 APTCA 特性和不应为供部分受信任的调用方 (由表示`M2`前面讨论)。  
  
 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]  
  
## <a name="example"></a>示例  
 第二个程序集是完全受信任，允许部分受信任的调用方 (由表示`M1`前面讨论)。  
  
 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]  
  
## <a name="example"></a>示例  
 测试应用程序 (由表示`X`前面讨论中) 是部分受信任。  
  
 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]  
  
 本示例生成以下输出。  
  
 **要求完全信任： 请求失败。**  
**调用 ClassRequiringFullTrust.DoWork 时。**   
## <a name="related-rules"></a>相关的规则  
 [CA2117：APTCA 类型应只扩展 APTCA 基类型](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)  
  
## <a name="see-also"></a>另请参阅  
 [安全编码准则](/dotnet/standard/security/secure-coding-guidelines)   
 [.NET framework 程序集可调用由部分受信任的代码](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [通过部分受信任的代码使用库](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)   
 [需求](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)   
 [链接需求](/dotnet/framework/misc/link-demands)   
 [数据和建模](/dotnet/framework/data/index)