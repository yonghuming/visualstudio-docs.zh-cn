---
title: "CA2130：安全关键常量应是透明的 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2130"
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2130：安全关键常量应是透明的
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 用 <xref:System.Security.SecurityCriticalAttribute> 标记的常数字段或枚举成员。  
  
## 规则说明  
 未对常数值实施透明强制，因为编译器内联常数值以便在运行时不需要查找。  常数字段应为安全透明的，以便代码评审阅者不会假定透明代码不能访问常数。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请从字段或值中移除 SecurityCritical 特性。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 在下面的示例中，枚举值 `EnumWithCriticalValues.CriticalEnumValue` 和常量 `CriticalConstant` 引发此警告。  若要修复该问题，删除 \[`SecurityCritical`\] 特性，以使其安全透明。  
  
 [!code-cs[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]