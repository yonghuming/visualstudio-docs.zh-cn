---
title: "“&lt;procedurename&gt;”没有任何参数，并且无法对它的返回类型进行索引 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32016"
  - "vbc32016"
helpviewer_keywords: 
  - "BC32016"
ms.assetid: beead513-c237-4c04-8a18-56f075b84712
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;procedurename&gt;”没有任何参数，并且无法对它的返回类型进行索引
对 `Function` 或 `Sub` 过程的调用提供一个或多个参数，但是该过程不采用任何参数，且其返回类型（如果它是 `Function`）不是一个数组类型。  
  
 **错误 ID：**BC32016  
  
### 更正此错误  
  
-   从过程调用中删除一个或多个参数。  
  
## 请参阅  
 [Sub 过程](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function 过程](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Function 语句](/dotnet/visual-basic/language-reference/statements/function-statement)   
 [Sub 语句](/dotnet/visual-basic/language-reference/statements/sub-statement)