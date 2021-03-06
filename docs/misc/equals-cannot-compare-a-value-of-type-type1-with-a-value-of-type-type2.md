---
title: "“Equals”不能对类型为 &lt;type1&gt; 的值与类型为 &lt;type2&gt; 的值进行比较 | Microsoft Docs"
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
  - "vbc36621"
  - "bc36621"
helpviewer_keywords: 
  - "BC36621"
ms.assetid: bd40bf57-3a12-407a-8622-7e428850c77c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Equals”不能对类型为 &lt;type1&gt; 的值与类型为 &lt;type2&gt; 的值进行比较
`Join` 或 `Group Join` 子句中的 `Equals` 运算符已尝试用未定义的方式将一种数据类型与另一种数据类型进行比较。 这种比较的一个示例是将 `Boolean` 值与 `Date` 类型进行比较。  
  
 **错误 ID：**BC36621  
  
### 更正此错误  
  
-   请确保 `Equals` 运算符每侧的值都可以转换为通用数据类型。 实现此目的的几个选项包括：  
  
    -   使用 `CType` 函数将一个或多个值转换为特定类型。  
  
    -   使用 <xref:System.Convert> 类或转换方法将一个或多个值转换为公共的、不可变的类型。  
  
    -   使用 `ToString` 方法将值转换为字符串。  
  
## 请参阅  
 [CType 函数](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Visual Basic 中的类型转换](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [Join 子句](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join 子句](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Visual Basic 中的 LINQ 简介](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)