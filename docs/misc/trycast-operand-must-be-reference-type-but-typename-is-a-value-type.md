---
title: "&quot;TryCast&quot; 操作数必须是引用类型，但“&lt;typename&gt;”是值类型 | Microsoft Docs"
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
  - "BC30792"
  - "vbc30792"
helpviewer_keywords: 
  - "BC30792"
ms.assetid: 3325fce5-dbc0-4d1d-9530-31f4720bfe6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;TryCast&quot; 操作数必须是引用类型，但“&lt;typename&gt;”是值类型
`TryCast` 运算符被用于至少一个参数的值类型。  
  
 `TryCast` 检测两个参数之间的继承关系或实现关系。 因此，它只能用于参数的引用类型。 有关更多信息，请参见[值类型和引用类型](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)。  
  
 **错误 ID：**BC30792  
  
### 更正此错误  
  
-   使用 `DirectCast` 或 `CType` 执行转换。 它们都可用于值类型。  
  
## 请参阅  
 [TryCast 运算符](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [DirectCast 运算符](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [CType 函数](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [值类型和引用类型](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)