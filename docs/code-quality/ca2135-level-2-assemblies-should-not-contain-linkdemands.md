---
title: "CA2135： 级别 2 程序集不应包含 Linkdemand |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2374b8de7e3d4f915f836f718b32dee028bee9ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135：级别 2 程序集不应包含 LinkDemand
|||  
|-|-|  
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2135|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 一个类或类成员使用<xref:System.Security.Permissions.SecurityAction>中的应用程序使用的第 2 级安全。  
  
## <a name="rule-description"></a>规则说明  
 在级别为 2 的安全规则集中已弃用 LinkDemand。 而不是使用 Linkdemand (在实时 JIT) 编译时强制安全性，将标记方法、 类型和字段与<xref:System.Security.SecurityCriticalAttribute>属性。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，移除<xref:System.Security.Permissions.SecurityAction>和标记的类型或成员<xref:System.Security.SecurityCriticalAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 在下面的示例中，<xref:System.Security.Permissions.SecurityAction>应删除，并且该方法标记为<xref:System.Security.SecurityCriticalAttribute>属性。  
  
 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]