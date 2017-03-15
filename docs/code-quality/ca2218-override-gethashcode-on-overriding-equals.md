---
title: "CA2218：重写 Equals 时重写 GetHashCode | Microsoft Docs"
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
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
helpviewer_keywords: 
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2218：重写 Equals 时重写 GetHashCode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|OverrideGetHashCodeOnOverridingEquals|  
|CheckId|CA2218|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 某公共类型重写 <xref:System.Object.Equals%2A?displayProperty=fullName> 但是不重写 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>。  
  
## 规则说明  
 <xref:System.Object.GetHashCode%2A> 基于适合哈希算法和诸如哈希表的数据结构的当前实例返回一个值。  两个相等的同类型对象必须返回相同的哈希代码，才能确保以下类型的实例正确运行：  
  
-   <xref:System.Collections.HashTable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortList?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybredDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   实现 <xref:System.Collections.Generic.IEqualityComparer?displayProperty=fullName> 的类型  
  
## 如何解决冲突  
 要修复与该规则的冲突，请提供 <xref:System.Object.GetHashCode%2A> 的实现。  对于一对相同类型的对象，如果 <xref:System.Object.Equals%2A> 的实现为该对对象返回 `true`，则必须确保该实现返回相同的值。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 类示例  
  
### 说明  
 下面的示例演示一个与此规则冲突的类（引用类型）。  
  
### 代码  
 [!code-cs[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### 注释  
 下面的示例通过重写 <xref:System.Object.GetHashCode> 修复冲突。  
  
### 代码  
 [!CODE [FxCop.Usage.GetHashCodeFixedClass#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass#1)]  
  
## 结构示例  
  
### 说明  
 下面的示例演示一个与此规则冲突的结构（值类型）。  
  
### 代码  
 [!code-cs[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
### 注释  
 下面的示例通过重写 <xref:System.Object.GetHashCode> 修复冲突。  
  
### 代码  
 [!code-cs[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
## 相关规则  
 [CA1046：不要对引用类型重载相等运算符](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225：运算符重载具有命名的备用项](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226：运算符应有对称重载](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224：重载相等运算符时重写 Equals 方法](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231：重写 ValueType.Equals 时应重载相等运算符](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## 请参阅  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.HashTable?displayProperty=fullName>   
 [相等运算符](../Topic/Equality%20Operators.md)