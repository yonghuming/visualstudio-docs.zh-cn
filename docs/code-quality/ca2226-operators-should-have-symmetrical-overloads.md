---
title: "CA2226：运算符应有对称重载 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperatorsShouldHaveSymmetricalOverloads"
  - "CA2226"
helpviewer_keywords: 
  - "CA2226"
  - "OperatorsShouldHaveSymmetricalOverloads"
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2226：运算符应有对称重载
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|OperatorsShouldHaveSymmetricalOverloads|  
|CheckId|CA2226|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 某个类型实现了相等运算符或不等运算符，却未实现相反运算符。  
  
## 规则说明  
 不能存在以下情况：相等运算符或不等运算符适用于某类型的实例，却未定义相反运算符。  类型通常通过返回相等运算符的反值来实现不等运算符。  
  
 C\# 编译器发出一个关于与该规则的冲突的错误。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请同时实现相等运算符和不等运算符，或者移除现有的运算符。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  您的类型的工作方式将与 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 不一致。  
  
## 相关规则  
 [CA1046：不要对引用类型重载相等运算符](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225：运算符重载具有命名的备用项](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2224：重载相等运算符时重写 Equals 方法](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218：重写 Equals 时重写 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231：重写 ValueType.Equals 时应重载相等运算符](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)