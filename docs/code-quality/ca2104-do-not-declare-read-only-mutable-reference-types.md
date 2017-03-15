---
title: "CA2104：不要声明只读可变引用类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
  - "CA2104"
helpviewer_keywords: 
  - "CA2104"
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2104：不要声明只读可变引用类型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|类别|Microsoft.Security|  
|是否重大更改|非重大更改|  
  
## 原因  
 外部可见类型包含外部可见的只读字段，该字段为可变的引用类型。  
  
## 规则说明  
 可变类型是实例数据可被修改的类型。  <xref:System.Text.StringBuilder?displayProperty=fullName> 类是可变引用类型的一个示例。  它包含可以更改类的实例值的成员。  不可变引用类型的一个示例是 <xref:System.String?displayProperty=fullName> 类。  当它被实例化以后，其值永远不能更改。  
  
 引用类型字段上的只读修饰符（在 C\# 中为 [readonly](/dotnet/csharp/language-reference/keywords/readonly)，在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)，在 C\+\+ 中为 [const](/visual-cpp/cpp/const-cpp)）的引用类型字段 （在 C\+\+ 中为指针） 可防止字段被替换为引用类型的不同实例。  但是，该修饰符不妨碍字段的实例数据通过引用类型得到修饰。  
  
 只读数组字段不受该规则限制，但是会导致与 [CA2105：数组字段不应为只读](../code-quality/ca2105-array-fields-should-not-be-read-only.md) 规则的冲突。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请移除只读修饰符，或者如果可以接受重大更改，请用不可变类型替换该字段。  
  
## 何时禁止显示警告  
 如果字段类型不可变，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示导致与该规则冲突的字段声明。  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-cs[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]