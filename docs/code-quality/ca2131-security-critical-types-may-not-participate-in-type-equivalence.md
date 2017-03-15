---
title: "CA2131：安全关键类型不能参与类型等效 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2131"
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2131：安全关键类型不能参与类型等效
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 类型参与了类型等价性，类型本身或类型的成员或字段用 <xref:System.Security.SecurityCriticalAttribute> 特性标记。  
  
## 规则说明  
 对于任何关键的类型或包含参与类型等效的关键方法或字段的类型，将引发此规则。  当 CLR 检测到这样的类型时，它未能在运行时使用 <xref:System.TypeLoadException> 加载它。  通常，仅在用户手动实现类型等效而不是通过依赖 tlbimp 和编译器进行类型等效时，才会触发此规则。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请删除 SecurityCritical 特性。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个接口、一个方法和导致触发此规则的字段。  
  
 [!code-cs[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## 请参阅  
 [安全透明的代码，级别 2](../Topic/Security-Transparent%20Code,%20Level%202.md)