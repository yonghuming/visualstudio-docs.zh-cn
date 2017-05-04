---
title: "“default”在“switch”语句中只能出现一次 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# “default”在“switch”语句中只能出现一次
尝试在 switch 语句中多次使用 **default** 语句。  default case 始终是 switch 语句中的最后一个 case 语句（它是直通 case 语句）。  
  
### 更正此错误  
  
-   从 `switch` 语句中移除任何多余的 **default** case 语句（通常在 switch 语句中最多使用一个 default case 语句）。  
  
## 请参阅  
 [switch 语句](../../javascript/reference/switch-statement-javascript.md)   
 [控制程序流](../../javascript/controlling-program-flow-javascript.md)   
 [JavaScript 保留字](../../javascript/reference/javascript-reserved-words.md)