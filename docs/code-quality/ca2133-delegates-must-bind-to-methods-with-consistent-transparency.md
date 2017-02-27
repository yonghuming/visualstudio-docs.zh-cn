---
title: "CA2133：委托必须绑定到具有一致透明度的方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2133"
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2133：委托必须绑定到具有一致透明度的方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
> [!NOTE]
>  此警告仅应用于运行 CoreCLR（特定于 Silverlight Web 应用程序的 CLR 版本）的代码。  
  
## 原因  
 在绑定委托的方法上会触发该警告，该委托用 <xref:System.Security.SecurityCriticalAttribute> 标记，并绑定给透明的方法，或用 <xref:System.Security.SecuritySafeCriticalAttribute> 标记的方法。  还会对另一个具有以下特点的方法引发此警告：该方法将透明的或安全关键的委托绑定到一个关键方法。  
  
## 规则说明  
 委托类型及其绑定的方法必须有一致的透明度。  透明和安全关键委托可能仅绑定到其他透明或关键安全方法。  相似地，关键委托可能仅将绑定到关键的方法。  这些绑定规则确保通过委托调用方法的唯一代码也已直接调用相同方法。  例如，绑定规则阻止透明代码直接通过透明委托调用关键代码。  
  
## 如何解决冲突  
 若要修复与该警告的冲突，请更改其绑定的委托或方法的透明度，使得二者的透明度等同。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
### 代码  
 [!code-cs[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]