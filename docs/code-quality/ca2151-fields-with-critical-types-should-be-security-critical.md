---
title: "CA2151：具有关键类型的字段应是安全关键的 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2151：具有关键类型的字段应是安全关键的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName||  
|CheckId|CA2151|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## 原因  
 声明了安全透明字段或可靠关键字段。  其类型被指定为安全关键。  例如：  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      Type1 m_field; // CA2151, transparent field of critical type  
   }  
  
```  
  
 在此示例中，`m_field` 是一个安全关键类型的安全透明字段。  
  
## 规则说明  
 若要使用安全关键类型，引用该类型的代码必须是安全关键或安全可靠关键。  即使引用是间接的，也需如此。  例如，当你引用具有关键类型的透明字段时，你的代码必须是安全关键的或安全可靠的。  因此，具有安全透明字段或安全可靠关键字段具有误导性，因为透明代码仍然无法访问该字段。  
  
## 如何解决冲突  
 若要解决此规则的冲突，请使用 <xref:System.Security.SecurityCriticalAttribute> 特性标记该字段，或将该字段引用的类型设为安全透明或安全关键。  
  
```c#  
// Fix 1: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
// Fix 2: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   class Type1 { } // Type1 is now transparent  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
```  
  
## 何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
### 代码  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]  
  
### 注释