---
title: "必须向该属性赋值或使用其值才能进行属性访问 | Microsoft Docs"
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
  - "bc30545"
  - "vbc30545"
helpviewer_keywords: 
  - "BC30545"
ms.assetid: df271c05-1e7a-44e8-bf53-79f06ef916ab
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必须向该属性赋值或使用其值才能进行属性访问
你已尝试在不为其赋值或不使用其值的情况下访问属性。 以下代码提供了一个示例：  
  
 [!CODE [VbVbalrErrorSamples#1](VbVbalrErrorSamples#1)]  
  
 **错误 ID：**BC30545  
  
### 更正此错误  
  
-   为该属性赋值，如下面的示例所示：  
  
     [!CODE [VbVbalrErrorSamples#3](VbVbalrErrorSamples#3)]  
  
     \- 或 \-  
  
-   使用该属性的值，如下面的示例所示：  
  
     [!CODE [VbVbalrErrorSamples#2](VbVbalrErrorSamples#2)]  
  
## 请参阅  
 [Property 过程](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [赋值运算符](/dotnet/visual-basic/language-reference/operators/assignment-operators)