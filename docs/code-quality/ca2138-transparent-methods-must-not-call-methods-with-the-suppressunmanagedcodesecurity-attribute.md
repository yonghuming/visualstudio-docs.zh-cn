---
title: "CA2138： 透明方法不得调用具有 SuppressUnmanagedCodeSecurity 特性的方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf17c69673649ac1f3af64bafcb718e8c84eb213
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138：透明方法不得调用具有 SuppressUnmanagedCodeSecurity 特性的方法
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 安全透明方法调用的方法，将标有<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性。  
  
## <a name="rule-description"></a>规则说明  
 直接调用到本机代码，例如，通过使用任何透明方法，将引发此规则通过使用 P/Invoke (平台 invoke) 调用。 P/Invoke 和 COM 互操作方法是，标记有<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性中进行调用的方法的 LinkDemand 结果。 由于安全透明代码不能满足 Linkdemand，代码还无法调用具有 SuppressUnmanagedCodeSecurity 特性标记的方法或方法的标记使用 SuppressUnmanagedCodeSecurity 特性的类。 该方法将失败，或需将转换为的完全要求。  
  
 违反此规则会导致<xref:System.MethodAccessException>级别 2 安全透明度模型中中的完全要求<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>级别 1 透明度模型中。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，移除<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性，此方法标记<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]