---
title: "“End While”前面必须是匹配的“While” | Microsoft Docs"
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
  - "vbc30090"
  - "bc30090"
helpviewer_keywords: 
  - "BC30090"
ms.assetid: 302b26b8-8fa4-4e49-86f0-d7c49fec485f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “End While”前面必须是匹配的“While”
出现 `End While` 语句而没有相应的 `While` 语句。`End While` 前面必须有相应的 `While` 语句。  
  
 **错误 ID：**BC30090  
  
### 更正此错误  
  
1.  如果此 `While` 块属于一组嵌套的 `While` 块，请确保每个块均已正确终止。  
  
2.  验证 `While` 块中的其他控制结构是否被正确终止。  
  
3.  确保此 `While` 块的格式正确。  
  
## 请参阅  
 [While...End While 语句](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)