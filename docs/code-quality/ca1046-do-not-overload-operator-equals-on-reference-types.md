---
title: "CA1046：不要对引用类型重载相等运算符 | Microsoft Docs"
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
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
  - "CA1046"
helpviewer_keywords: 
  - "CA1046"
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1046：不要对引用类型重载相等运算符
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 公共或嵌套公共引用类型重载了相等运算符。  
  
## 规则说明  
 对于引用类型，相等运算符的默认实现几乎始终是正确的。  默认情况下，仅当两个引用指向同一对象时，它们才相等。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请移除相等运算符的实现。  
  
## 何时禁止显示警告  
 当引用类型的工作方式类似于内置值类型时，可以安全地禁止显示此规则发出的警告。  如果对类型的实例进行相加或相减有意义，则实现相等运算符并禁止显示冲突可能是正确的。  
  
## 示例  
 下面的示例演示比较两个引用时的默认行为。  
  
 [!code-cs[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## 示例  
 下面的应用程序比较一些引用。  
  
 [!code-cs[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 该示例产生下面的输出。  
  
  **a \= new \(2,2\) and b \= new \(2,2\) are equal?  否**  
**c and a are equal?  是**  
**b 和 a 为 \=\= ?  否**  
**c 和 a 为 \=\= ?  是**    
## 相关规则  
 [CA1013：重载加法方法和减法方法时重载相等运算符](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## 请参阅  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [相等运算符](../Topic/Equality%20Operators.md)