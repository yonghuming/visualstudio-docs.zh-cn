---
title: "“Sub”不返回值，因此在“Sub”声明中不能使用类型字符 | Microsoft Docs"
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
  - "bc30303"
  - "vbc30303"
helpviewer_keywords: 
  - "BC30303"
ms.assetid: f5a744f0-d312-4fe3-90cd-3cf372a93664
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Sub”不返回值，因此在“Sub”声明中不能使用类型字符
`Sub` 过程（如 `Function` 过程）是可以采用参数并执行一系列语句的单独过程。 与 `Function` 过程不同，`Sub` 不返回值，因此不能包含类型声明。  
  
 **错误 ID：**BC30303  
  
### 更正此错误  
  
-   将 `Function` 过程改为 `Sub` 过程。  
  
## 请参阅  
 [Sub 过程](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function 过程](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)