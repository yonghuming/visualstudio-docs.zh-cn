---
title: "“Loop”和匹配的“Do”不能同时具有条件 | Microsoft Docs"
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
  - "vbc30238"
  - "bc30238"
helpviewer_keywords: 
  - "BC30238"
ms.assetid: 81513cb5-69e7-4d62-b33e-e54cb8c5e8bf
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Loop”和匹配的“Do”不能同时具有条件
`Loop` 语句包含 `While` 或 `Until` 子句，相应的 `Do` 语句也包含此类子句。 一个循环中只有 `Do` 和 `Loop` 中的其中一个语句可以指定条件。  
  
 **错误 ID：**BC30238  
  
### 更正此错误  
  
-   从 `Do` 语句或 `Loop` 语句中删除 `While` 或 `Until` 子句。  
  
## 请参阅  
 [Do...Loop 语句](/dotnet/visual-basic/language-reference/statements/do-loop-statement)