---
title: "“Else”前面必须是匹配的“If”或“ElseIf” | Microsoft Docs"
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
  - "bc30086"
  - "vbc30086"
helpviewer_keywords: 
  - "BC30086"
ms.assetid: 5e76b3c6-571f-4a6f-b524-26150cb6e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Else”前面必须是匹配的“If”或“ElseIf”
出现 `Else` 语句而没有相应的 `If` 语句。`Else` 前面必须是 `If` 语句。  
  
 **错误 ID：**BC30086  
  
### 更正此错误  
  
1.  如果此 `If` 块属于一组嵌套的 `If` 块，请确保每个块均已正确终止。  
  
2.  验证 `If` 块中的其他控制结构是否被正确终止。  
  
3.  确保此 `If` 块的格式正确。  
  
## 请参阅  
 [If...Then...Else 语句](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)