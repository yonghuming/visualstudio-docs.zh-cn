---
title: "“End Using”前面必须是匹配的“Using” | Microsoft Docs"
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
  - "bc36007"
  - "vbc36007"
helpviewer_keywords: 
  - "BC36007"
ms.assetid: 10fb31ba-9b6c-403f-bacc-c7b5df14f1dd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “End Using”前面必须是匹配的“Using”
`End Using` 语句前面没有任何匹配的 `Using` 声明。  
  
 **错误 ID：**BC36007  
  
### 更正此错误  
  
-   删除多余的 `End Using` 语句。  
  
-   提供缺少的 [Using 语句](/dotnet/visual-basic/language-reference/statements/using-statement)（如果有）。  
  
-   将 `End Using` 语句移到代码中的适当位置。  
  
## 请参阅  
 [End \<关键字\> 语句](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)