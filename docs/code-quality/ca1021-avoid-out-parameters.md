---
title: "CA1021：避免使用 out 参数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1021"
  - "AvoidOutParameters"
helpviewer_keywords: 
  - "AvoidOutParameters"
  - "CA1021"
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1021：避免使用 out 参数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidOutParameters|  
|CheckId|CA1021|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 公共类型中的某公共方法或受保护方法具有 `out` 参数。  
  
## 规则说明  
 通过引用（使用 `out` 或 `ref`）传递类型有以下要求：具有使用指针的经验，了解值类型和引用类型的不同之处，以及如何处理具有多个返回值的方法。  另外，`out` 和 `ref` 参数之间的差异没有得到广泛了解。  
  
 当“按引用”传递引用类型时，方法希望使用参数来返回对象的另一个实例。  按引用传递引用类型也称为使用双指针、指向指针的指针或双间接寻址。  通过使用默认调用约定，即“按值”传递，接受引用类型的参数已接收到指向对象的指针。  值传递的是指针，而不是指针所指向的对象。  通过值传递意味着方法无法将指针更改为指向引用类型的新实例。  但是，它能够更改所指向的对象的内容。  对于大多数应用程序，这是足够的并且能够产生所需的行为。  
  
 如果某方法必须返回不同的实例，请使用该方法的返回值完成此操作。  有关对字符串进行操作和返回字符串的新实例的各种方法，请参见 <xref:System.String?displayProperty=fullName> 类。  如果使用此模型，则调用方必须决定是否保留原始对象。  
  
 虽然返回值比较常见并经常使用，但正确应用 `out` 和 `ref` 参数需要中间设计和编码技能。  针对普通用户进行设计的库架构师不应期望用户掌握了 `out` 或 `ref` 参数的使用方法。  
  
## 如何解决冲突  
 要修复由值类型导致的与该规则的冲突，请让方法将对象作为其返回值返回。  如果方法必须返回多个值，请重新设计该方法以返回包含这些值的对象的单个实例。  
  
 要修复由引用类型导致的与该规则的冲突，请确保您需要的行为是返回引用的新实例。  如果确实如此，则方法应使用其返回值来进行此操作。  
  
## 何时禁止显示警告  
 可以安全地禁止显示此规则发出的警告。  但是，这种设计可能导致可用性问题。  
  
## 示例  
 下面的库演示对用户反馈生成响应的类的两种实现方式。  第一个实现 \(`BadRefAndOut`\) 强制库用户管理三个返回值。  第二个实现 \(`RedesignedRefAndOut`\) 通过返回将数据作为单个单元进行管理的容器类 \(`ReplyData`\) 的实例，来简化用户体验。  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]  
  
## 示例  
 下面的应用程序阐释了用户的体验。  调用重新设计的库的过程（`UseTheSimplifiedClass` 方法）更加简单，而且由该方法返回的信息更加易于管理。  两个方法的输出是相同的。  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]  
  
## 示例  
 下面的示例库阐释如何使用引用类型的 `ref` 参数，并演示一种更好地实现该功能的方法。  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]  
  
## 示例  
 下面的应用程序调用库中的每个方法来演示该行为。  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]  
  
 该示例产生下面的输出。  
  
  **Changing pointer \- passed by value:**  
**12345**  
**12345**  
**Changing pointer \- passed by reference:**  
**12345**  
**12345 ABCDE**  
**Passing by return value:**  
**12345 ABCDE**   
## Try 模式方法  
  
### 说明  
 实现 **Try\<Something\>** 模式，例如<xref:System.Int32.TryParse%2A?displayProperty=fullName>，不会引发此冲突。  下面的示例演示一个实现 <xref:System.Int32.TryParse%2A?displayProperty=fullName> 方法的结构（值类型）。  
  
### 代码  
 [!CODE [FxCop.Design.TryPattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern#1)]  
  
## 相关规则  
 [CA1045：不要通过引用来传递类型](../code-quality/ca1045-do-not-pass-types-by-reference.md)