---
title: "CA2146：类型必须至少与其基类型和接口一样关键 | Microsoft Docs"
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
  - "CA2146"
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2146：类型必须至少与其基类型和接口一样关键
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|CheckId|CA2146|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 透明类型派生自用 <xref:System.Security.SecuritySafeCriticalAttribute> 或 <xref:System.Security.SecurityCriticalAttribute> 标记的类型，或者说用 <xref:System.Security.SecuritySafeCriticalAttribute> 特性标记的类型派生自用 <xref:System.Security.SecurityCriticalAttribute> 标记的特性。  
  
## 规则说明  
 当派生类型具有的安全透明特性与其基类型或实现的接口不是同样关键时，将引发此规则。  只有关键类型可以从关键基类型派生或实现关键接口，并且只有关键或关键安全类型可以从安全关键基类型派生或实现关键安全接口。  在级别 2 透明度违反此规则导致派生类型的 <xref:System.TypeLoadException>。  
  
## 如何解决冲突  
 若要修复此冲突，用透明特性标记派生或实现类型，其至少与基类或接口一样关键。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 [!CODE [FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes#1)]