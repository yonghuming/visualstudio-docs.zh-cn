---
title: "未终止的注释 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 未终止的注释
已开始一个多行注释块，但未正确将其终止。  多行注释以“\/\*”组合开头，以反序的“\*\/”组合结尾。  下面是一个示例：  
  
```javascript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### 更正此错误  
  
-   确保多行注释以“\*\/”终止。  
  
## 请参阅  
 [注释语句](../../javascript/reference/comment-statements-javascript.md)