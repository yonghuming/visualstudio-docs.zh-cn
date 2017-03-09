---
title: "应为“Equals” | Microsoft Docs"
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
  - "vbc36619"
  - "bc36619"
helpviewer_keywords: 
  - "BC36619"
ms.assetid: 1fd8c0dc-0e87-47b7-ab30-498809cca033
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 应为“Equals”
已经指定 `Join` 或 `Group Join` 子句，但没有使用 `Equals` 运算符。 使用 `Equals` 运算符来标识 `Boolean` 操作以测试匹配项的键字段。  
  
 **错误 ID：**BC36619  
  
### 更正此错误  
  
1.  将 `Equals` 运算符和键字段添加到 `Join` 或 `Group Join` 子句。 例如:  
  
    ```vb#  
    Dim petOwnersGrouped = From pers In people _ Group Join pet In pets _ On pers Equals pet.Owner _ Into PetList = Group _ Select pers.FirstName, pers.LastName, _ PetList  
    ```  
  
## 请参阅  
 [如何：使用联接合并数据](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join 子句](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join 子句](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Visual Basic 中的 LINQ 简介](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)