---
title: "“Exit”的后面必须跟有“Sub”、“Function”、“Property”、“Do”、“For”、“While”、“Select”或“Try” | Microsoft Docs"
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
  - "bc30240"
  - "vbc30240"
helpviewer_keywords: 
  - "BC30240"
ms.assetid: 91078689-f4bf-4331-a475-10bc9fe7cd0c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Exit”的后面必须跟有“Sub”、“Function”、“Property”、“Do”、“For”、“While”、“Select”或“Try”
`Exit` 语句包含无效的关键字。`Exit` 必须指定要将控制权从其转移到其后的语句的块，例如 `End While`。  
  
 **错误 ID：**BC30240  
  
### 更正此错误  
  
-   在 `Exit` 后添加有效关键字，或删除 `Exit` 语句。  
  
## 请参阅  
 [Exit 语句](/dotnet/visual-basic/language-reference/statements/exit-statement)