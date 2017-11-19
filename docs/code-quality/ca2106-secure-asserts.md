---
title: "CA2106： 保护断言 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 321d00f13ebc891070549778239fec60201d03c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2106-secure-asserts"></a>CA2106：保护断言
|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 某个方法断言权限，但不对调用方执行任何安全检查。  
  
## <a name="rule-description"></a>规则说明  
 如果在不执行任何安全检查的情况下断言安全权限，则会在代码中留下可利用的安全漏洞。 安全堆栈审核将停止时对以下安全权限进行断言。 如果在调用方执行任何检查的情况下断言权限，调用方无法通过使用你的权限间接地执行代码。 断言无安全检查是允许仅当你确信，该断言不能有害的方式。 声明是无害的如果您调用的代码不会造成损害，或用户不能将任意信息传递给调用的代码。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，添加对方法或其声明的类型安全要求。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 禁止显示此规则仅在仔细的安全检查后的警告。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [安全编码准则](/dotnet/standard/security/secure-coding-guidelines)