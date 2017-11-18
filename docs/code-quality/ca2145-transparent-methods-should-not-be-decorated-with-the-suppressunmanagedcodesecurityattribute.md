---
title: "CA2145： 透明方法应不使用 SuppressUnmanagedCodeSecurityAttribute 修饰 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 23cf7599e4d699a6be42bae55381ffb31ce1556e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145：不应使用 SuppressUnmanagedCodeSecurityAttribute 修饰透明方法
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 透明方法，将标有方法<xref:System.Security.SecuritySafeCriticalAttribute>方法或包含一个方法的类型将标有<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性。  
  
## <a name="rule-description"></a>规则说明  
 使用修饰方法<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性有一个隐式的 LinkDemand 作用于调用它的任何方法。 此 LinkDemand 要求调用代码是关键安全的。 标记使用 SuppressUnmanagedCodeSecurity 的方法<xref:System.Security.SecurityCriticalAttribute>特性使此要求更明显方法的调用方。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，标记该方法或类型具有<xref:System.Security.SecurityCriticalAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### <a name="comments"></a>注释