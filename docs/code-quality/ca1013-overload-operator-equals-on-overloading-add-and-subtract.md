---
title: "CA1013：重载加法方法和减法方法时重载相等运算符 | Microsoft Docs"
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
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
helpviewer_keywords: 
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1013：重载加法方法和减法方法时重载相等运算符
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 公共或受保护类型实现加或减运算符时没有实现相等运算符。  
  
## 规则说明  
 当类型的实例可以使用运算（例如加或减）连接起来时，应当始终定义相等，以便为有相同的组成值的两个实例返回 `true`。  
  
 不能在相等运算符的重载实现中使用默认相等运算符。  这样做将会导致堆栈溢出。  要实现相等运算符，请在实现中使用 Object.Equals 方法。  请参见下面的示例。  
  
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
 要修复与该规则的冲突，请实现相等运算符，使它与加和减运算符在数学上一致。  
  
## 何时禁止显示警告  
 当相等运算符的默认实现为类型提供正确行为时，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例定义一个与该规则冲突的类型 \(`BadAddableType`\)。  此类型应当实现相等运算符，使任意两个有相同字段值的实例测试为 `true` 来说明它们相等。  类型 `GoodAddableType` 演示了更正的实现。  请注意，此类型还实现不等运算符并重写 <xref:System.Object.Equals%2A> 以满足其他规则。  一个完整的实现还将实现 <xref:System.Object.GetHashCode%2A>。  
  
 [!code-cs[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## 示例  
 下面的示例使用本主题前面定义的类型的实例测试是否相等，以阐释相等运算符的默认行为和正确行为。  
  
 [!code-cs[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 该示例产生下面的输出。  
  
  **Bad type:  {2,2} {2,2} are equal?  否**  
**Good type: {3,3} {3,3} are equal?  是**  
**Good type: {3,3} {3,3} are \=\= ?是**  
**Bad type:  {2,2} {9,9} are equal?  否**  
**Good type: {3,3} {9,9} are \=\= ?否**    
## 请参阅  
 [相等运算符](../Topic/Equality%20Operators.md)