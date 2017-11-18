---
title: "CA2140： 透明代码不得引用安全关键项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e11167ba35baf8802709d0d65b9b4045ede25126
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140：透明代码不得引用安全关键项
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 透明的方法：  
  
-   处理安全关键安全异常类型  
  
-   具有标记为安全关键类型的参数  
  
-   具有安全关键约束的泛型参数  
  
-   具有的安全关键类型的局部变量  
  
-   引用了被标记为安全关键的类型  
  
-   调用被标记为安全关键的方法  
  
-   引用被标记为安全关键的字段  
  
-   返回被标记为安全关键的类型  
  
## <a name="rule-description"></a>规则说明  
 将标有一个代码元素<xref:System.Security.SecurityCriticalAttribute>是安全关键的属性。 透明方法不能使用安全关键元素。 如果透明类型尝试使用安全关键类型<xref:System.TypeAccessException>， <xref:System.MethodAccessException> ，或<xref:System.FieldAccessException>引发。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请执行以下操作：  
  
-   将使用与对安全关键代码的代码元素的标记<xref:System.Security.SecurityCriticalAttribute>属性  
  
     \- 或 -  
  
-   删除<xref:System.Security.SecurityCriticalAttribute>从被标记为安全关键，而是将其与标记的代码元素的属性<xref:System.Security.SecuritySafeCriticalAttribute>或<xref:System.Security.SecurityTransparentAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 在以下示例中，透明方法尝试引用安全关键泛型集合、 安全的关键领域和安全关键方法。  
  
 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>