---
title: "CA2134：在重写基方法时，方法必须保持一致的透明度 | Microsoft Docs"
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
  - "CA2134"
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2134：在重写基方法时，方法必须保持一致的透明度
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 当方法是透明的或标记有 <xref:System.Security.SecurityCriticalAttribute> 并覆盖透明方法或标记有 <xref:System.Security.SecuritySafeCriticalAttribute> 的方法时，该规则也会被触发。  当方法是透明的或标记有 <xref:System.Security.SecuritySafeCriticalAttribute> 并覆盖标记有 <xref:System.Security.SecurityCriticalAttribute> 的方法时，该规则也会被触发。  
  
 该规则在重写虚方法或实现接口时应用。  
  
## 规则说明  
 尝试更改方法的安全性辅助功能（进一步在继承链中）会激发此规则。  例如，如果基类中的虚拟方法为透明的或安全关键，那么派生类必须用透明或关键安全方法重写它。  相反，如果虚拟为安全关键，则派生的类必须用安全关键方法覆盖。  相同的规则应用于实现接口方法。  
  
 代码是 JIT 编译而不是在运行时编译，以便透明度计算不具有动态类型信息时，会强制执行透明度规则。  因此，透明度计算结果必须能够仅从正在 JIT 编译的静态类型确定，无论动态类型如何。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，更改方法的透明度，其被重写虚拟方法或实现接口以匹配虚拟或接口方法的透明度。  
  
## 何时禁止显示警告  
 不要禁止显示与此规则有关的警告。  违反此规则将导致使用级别 2 透明度的程序集的运行时 <xref:System.TypeLoadException>。  
  
## 示例  
  
### 代码  
 [!CODE [FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency#1)]  
  
## 请参阅  
 [安全透明的代码，级别 2](../Topic/Security-Transparent%20Code,%20Level%202.md)