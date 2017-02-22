---
title: "CA2224：重载相等运算符时重写 Equals 方法 | Microsoft Docs"
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
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
  - "OverrideEqualsOnOverridingOperatorEquals"
helpviewer_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2224：重载相等运算符时重写 Equals 方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 某公共类型实现了等号运算符，但是没有重写 <xref:System.Object.Equals%2A?displayProperty=fullName>。  
  
## 规则说明  
 相等运算符旨在为访问 <xref:System.Object.Equals%2A> 方法的功能提供一种易于使用的语法。  如果实现等号运算符，其逻辑必须与 <xref:System.Object.Equals%2A> 的逻辑相同。  
  
 如果代码与该规则冲突，C\# 编译器将发出警告。  
  
## 如何解决冲突  
 要修复与该规则的冲突，应当移除等号运算符的实现过程，或重写 <xref:System.Object.Equals%2A>，使这两种方法返回相同的值。  如果等号运算符没有引入不一致的行为，可以通过调用基类中的 <xref:System.Object.Equals%2A> 方法来实现 <xref:System.Object.Equals%2A>，以此修复冲突。  
  
## 何时禁止显示警告  
 如果等号运算符与继承的 <xref:System.Object.Equals%2A> 的实现返回相同的值，则可以安全地禁止显示与该规则有关的警告。  “示例”部分包含一个可以安全地禁止显示与该规则有关的警告的类型。  
  
## 不一致相等定义示例  
  
### 说明  
 下面的示例演示一个具有不一致的相等的定义的类型。  `BadPoint` 通过提供等号运算符的自定义实现更改了相等的含义，但是没有重写 <xref:System.Object.Equals%2A> 以使它具有相同的行为。  
  
### 代码  
 [!code-cs[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## 示例  
 下面的代码测试 `BadPoint` 的行为。  
  
 [!code-cs[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 该示例产生下面的输出。  
  
  **a \=  \(\[0\] 1,1\) and b \= \(\[1\] 2,2\) are equal?  否**  
**a \=\= b ?  否**  
**a1 and a are equal?  是**  
**a1 \=\= a ?  是**  
**b and bcopy are equal ?  否**  
**b \=\= bcopy ?  是**    
## 示例  
 下面的示例演示一个从技术上说违反了该规则，但是在行为上保持一致的类型。  
  
 [!code-cs[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## 示例  
 下面的代码测试 `GoodPoint` 的行为。  
  
 [!code-cs[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 该示例产生下面的输出。  
  
  **a \=  \(1,1\) and b \= \(2,2\) are equal?  否**  
**a \=\= b ?  否**  
**a1 and a are equal?  是**  
**a1 \=\= a ?  是**  
**b and bcopy are equal ?  是**  
**b \=\= bcopy ?  是**    
## 类示例  
  
### 说明  
 下面的示例演示一个与此规则冲突的类（引用类型）。  
  
### 代码  
 [!code-cs[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## 示例  
 下面的示例通过重写 <xref:System.Object.Equals%2A?displayProperty=fullName> 修复冲突。  
  
 [!code-cs[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## 结构示例  
  
### 说明  
 下面的示例演示一个与此规则冲突的结构（值类型）。  
  
### 代码  
 [!code-cs[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## 示例  
 下面的示例通过重写 <xref:System.ValueType.Equals%2A?displayProperty=fullName> 修复冲突。  
  
 [!code-cs[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## 相关规则  
 [CA1046：不要对引用类型重载相等运算符](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225：运算符重载具有命名的备用项](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226：运算符应有对称重载](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218：重写 Equals 时重写 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231：重写 ValueType.Equals 时应重载相等运算符](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)