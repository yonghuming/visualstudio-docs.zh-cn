---
title: "CA2105：数组字段不应为只读 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2105"
  - "ArrayFieldsShouldNotBeReadOnly"
helpviewer_keywords: 
  - "ArrayFieldsShouldNotBeReadOnly"
  - "CA2105"
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2105：数组字段不应为只读
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ArrayFieldsShouldNotBeReadOnly|  
|CheckId|CA2105|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 用于存放数组的公共或受保护的字段声明为只读。  
  
## 规则说明  
 向包含数组的字段应用 `readonly`（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 `ReadOnly`）修饰符时，无法将该字段更改为引用其他数组。  但是，可以更改在只读字段中存储的数组的元素。  用于基于公共可访问的只读数组的元素做出决定或执行操作的代码可能包含可利用的安全漏洞。  
  
 请注意，使用公共字段还会与设计规则 [CA1051：不要声明可见实例字段](../code-quality/ca1051-do-not-declare-visible-instance-fields.md) 冲突。  
  
## 如何解决冲突  
 要修复由该规则标识的安全漏洞，请不要依赖于可公开访问的只读数组的内容。  强烈建议您使用以下过程之一：  
  
-   将数组替换为无法被更改的强类型集合。  有关更多信息，请参见 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>。  
  
-   将公共字段替换为返回私有数组副本的方法。  由于代码不依赖于副本，即使修改元素也不会产生任何危险。  
  
 如果选择第二种方法，请不要使用属性替换该字段；使用返回数组的属性会对性能造成负面影响。  有关更多信息，请参见 [CA1819：属性不应返回数组](../code-quality/ca1819-properties-should-not-return-arrays.md)。  
  
## 何时禁止显示警告  
 强烈建议不要排除与该规则有关的警告。  几乎在任何情况下，只读字段中的内容都是非常重要的。  如果您遇到此情况，请移除 `readonly` 修饰符，而不要排除该消息。  
  
## 示例  
 此示例演示违反该规则的危险。  第一部分演示具有类型 `MyClassWithReadOnlyArrayField` 的示例库，它包含两个不安全的字段（`grades` 和 `privateGrades`）。  字段 `grades` 为公共字段，因此很容易受到任何调用方的攻击。  字段 `privateGrades` 为私有字段，但因为该字段被 `GetPrivateGrades` 方法返回给调用方，因此仍然很容易受到攻击。  `securePrivateGrades` 字段通过 `GetSecurePrivateGrades` 方法以安全方式进行公开。  该字段声明为私有字段，这是一种良好的设计习惯。  第二部分演示的代码将更改存储于 `grades` 和 `privateGrades` 成员中的值。  
  
 下面的示例中显示了示例类库。  
  
 [!code-cs[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## 示例  
 下面的代码使用示例类库阐释只读数组的安全问题。  
  
 [!code-cs[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 此示例的输出为：  
  
  **Before tampering: Grades: 90, 90, 90 Private Grades: 90, 90, 90  Secure Grades, 90, 90, 90**  
**After tampering: Grades: 90, 555, 90 Private Grades: 90, 555, 90  Secure Grades, 90, 90, 90**   
## 请参阅  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>