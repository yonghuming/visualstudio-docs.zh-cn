---
title: "必须在“Equals”运算符的两侧引用至少一个范围变量 | Microsoft Docs"
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
  - "vbc36622"
  - "bc36622"
helpviewer_keywords: 
  - "BC36622"
ms.assetid: 8d301227-131d-4977-b3ff-1fc4e427f8fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必须在“Equals”运算符的两侧引用至少一个范围变量
必须在“Equals”运算符的两侧引用至少一个范围变量。 范围变量 \<variable\> 必须在“Equals”运算符的一侧出现，范围变量 \<variable\> 必须在另一侧上出现。  
  
 为要在 LINQ 查询中联接的集合标识的范围变量必须位于 `Equals` 运算符的另一侧，具体取决于标识它们所为的集合。 也就是说，为被联接集合之一所标识的范围变量与另一个被联接集合的范围变量必须位于 `Equals` 运算符的对侧。 来自不同集合的范围变量不能在 `Equals` 运算符的同侧混合。  
  
 `Equals` 运算符每侧必须引用来自被联接集合的至少一个变量。  
  
 **错误 ID：**BC36622  
  
## 请参阅  
 [Visual Basic 中的 LINQ 简介](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)   
 [Join 子句](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join 子句](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [From 子句](/dotnet/visual-basic/language-reference/queries/from-clause)   
 [Select 子句](/dotnet/visual-basic/language-reference/queries/select-clause)