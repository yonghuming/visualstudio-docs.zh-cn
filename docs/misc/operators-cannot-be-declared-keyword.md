---
title: "运算符不能声明为“&lt;keyword&gt;”。 | Microsoft Docs"
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
  - "vbc33013"
  - "bc33013"
helpviewer_keywords: 
  - "BC33013"
ms.assetid: bfd805f4-e30e-4553-9cb7-2690595f0480
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 运算符不能声明为“&lt;keyword&gt;”。
使用对于运算符定义无效的关键字声明运算符。  
  
 每个运算符必须声明为 [Public](/dotnet/visual-basic/language-reference/modifiers/public) 和 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)。 此外，可使用任一 [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) 或 [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) 声明转换运算符，但不可同时使用两者。 运算符定义可以选择性地包含 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) 或 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) 关键字。 在 [Operator 语句](/dotnet/visual-basic/language-reference/statements/operator-statement) 中不允许有其他关键字。  
  
 **错误 ID：**BC33013  
  
### 更正此错误  
  
-   从运算符定义中删除无效关键字。  
  
## 请参阅  
 [运算符过程](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)