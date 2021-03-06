---
title: "无法推断“&lt;genericprocedurename&gt;”的类型形参“&lt;typeparametername&gt;” | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32050"
  - "bc32050"
helpviewer_keywords: 
  - "BC32050"
ms.assetid: e4a69ffb-0764-4e5a-8de1-40f881a3f4fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法推断“&lt;genericprocedurename&gt;”的类型形参“&lt;typeparametername&gt;”
在未提供类型实参列表的情况下调用泛型过程，某个类型实参的类型推理失败。  
  
 在调用泛型过程时，通常会为过程所定义的每个类型形参提供类型实参。 但是，还可以选择忽略整个类型实参列表。 执行此操作时，编译器将尝试推断调用上下文中每个类型实参的类型。 有关详细信息，请参见 [Visual Basic 中的泛型过程](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures) 中的“类型推理”。  
  
 导致类型推理失败的一个可能原因是类型形参和调用类型之间的等级不匹配。 下面的代码阐释这一点。  
  
```  
Public Sub displayLargest(Of t As IComparable)(ByVal arg() As t) ' Insert code to find and display the largest element of arg(). End Sub Public Sub callGenericSub() Dim testValue As Integer findLargest(testValue) Dim testMatrix(,) As Integer findLargest(testMatrix) End Sub  
```  
  
 在前面的代码中，两次对 `findLargest` 的调用均产生此错误，因为类型形参 `t` 调用的是一维数组，而编译器从调用推断出的类型实参是一个标量 \(`testValue`\) 和一个二维数组 \(`testMatrix`\)。  
  
 **错误 ID：**BC32050  
  
### 更正此错误  
  
-   确保普通参数的类型是这样的：类型推理与为泛型过程声明的类型形参一致。  
  
     \- 或 \-  
  
-   调用具有完整类型实参列表的泛型过程，因此就不需要类型推理。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [类型列表](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Visual Basic 中的泛型过程](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)