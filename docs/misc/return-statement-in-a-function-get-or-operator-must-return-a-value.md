---
title: "Function、Get 或 Operator 中的“Return”语句必须返回值 | Microsoft Docs"
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
  - "bc30654"
  - "vbc30654"
helpviewer_keywords: 
  - "BC30654"
ms.assetid: af0fb1fc-1b2e-4cae-9768-10965cda5506
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Function、Get 或 Operator 中的“Return”语句必须返回值
`Return` 语句必须用于返回调用过程的值。 不能使用 `Return` 语句本身来控制程序流。  
  
 **错误 ID：**BC30654  
  
### 更正此错误  
  
1.  指定可返回函数或过程的值。  
  
2.  使用 `End` 语句，以使程序退出当前过程。  
  
## 请参阅  
 [Return 语句](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [End \<关键字\> 语句](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)