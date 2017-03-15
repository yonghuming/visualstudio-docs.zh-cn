---
title: "CA2132：默认构造函数必须至少与基类型默认构造函数具有同样的关键性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2132"
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2132：默认构造函数必须至少与基类型默认构造函数具有同样的关键性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
> [!NOTE]
>  此警告仅应用于运行 CoreCLR（特定于 Silverlight Web 应用程序的 CLR 版本）的代码。  
  
## 原因  
 派生类的默认构造函数的透明特性不是和基类的透明度一样关键的。  
  
## 规则说明  
 具有 <xref:System.Security.SecurityCriticalAttribute> 的类型和成员无法供 Silverlight 应用程序代码使用。  安全关键类型和成员只能供 .NET Framework for Silverlight 类库中的受信任代码使用。  因为派生类中的某个公共或受保护构造必须有与其基类相同或更大的透明度，所以不能从标记为 SecurityCritical 的类派生应用程序中的类。  
  
 对于 CoreCLR 平台代码，如果基类型有公共或受保护的非透明默认构造函数，那么派生的类型必须遵循默认构造函数继承规则。  派生的类型还必须具有默认构造函数，该构造函数必须至少为基类型的关键默认构造函数。  
  
## 如何解决冲突  
 若要修复此冲突，删除类型或不从安全非透明类型派生。  
  
## 何时禁止显示警告  
 不要禁止显示与此规则有关的警告。  应用程序违反该规则将导致 CoreCLR 拒绝加载具有 <xref:System.TypeLoadException> 的类型。  
  
### 代码  
 [!CODE [FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency#1)]  
  
### 注释