---
title: "&lt;error&gt;：“&lt;classname1&gt;”继承自“&lt;classname2&gt;” | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30256"
  - "vbc30256"
helpviewer_keywords: 
  - "BC30256"
ms.assetid: 170a12ee-87ef-4a49-8c84-ebf57fac435e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;error&gt;：“&lt;classname1&gt;”继承自“&lt;classname2&gt;”
检测到循环继承层次结构。 类被指定为继承自自身，或继承自另一直接或最终继承自它的类。  
  
 可以多次出现此消息，以跟踪循环继承路径。  
  
 **错误 ID：**BC30256  
  
### 更正此错误  
  
-   通过删除循环继承路径中至少一个 `Inherits` 语句中断循环。  
  
## 请参阅  
 [继承的基础知识](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)