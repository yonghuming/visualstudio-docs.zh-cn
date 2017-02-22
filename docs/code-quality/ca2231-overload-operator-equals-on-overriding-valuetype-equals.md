---
title: "CA2231：重写 ValueType.Equals 时应重载相等运算符 | Microsoft Docs"
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
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
  - "CA2231"
  - "OverrideOperatorEqualsOnOverridingValueTypeEquals"
helpviewer_keywords: 
  - "CA2231"
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2231：重写 ValueType.Equals 时应重载相等运算符
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 值类型重载 <xref:System.Object.Equals%2A?displayProperty=fullName> 但无法实现相等运算符。  
  
## 规则说明  
 大多数编程语言中都没有用于值类型的默认相等运算符 \(\=\=\) 实现。  如果编程语言支持运算符重载，则应考虑实现相等运算符。  该运算符的行为必须与 <xref:System.Object.Equals%2A> 的行为相同。  
  
 不能在相等运算符的重载实现中使用默认相等运算符。  这样做将会导致堆栈溢出。  要实现相等运算符，请在实现中使用 Object.Equals 方法。  例如：  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```c#  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## 如何解决冲突  
 要修复与该规则的冲突，请实现相等运算符。  
  
## 何时禁止显示警告  
 可以安全地禁止显示此规则发出的警告；但是建议您尽可能提供相等运算符。  
  
## 示例  
 下面的示例定义一个与该规则冲突的类型。  
  
 [!CODE [FxCop.Usage.EqualsGetHashCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode#1)]  
  
## 相关规则  
 [CA1046：不要对引用类型重载相等运算符](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225：运算符重载具有命名的备用项](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226：运算符应有对称重载](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224：重载相等运算符时重写 Equals 方法](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218：重写 Equals 时重写 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## 请参阅  
 <xref:System.Object.Equals%2A?displayProperty=fullName>