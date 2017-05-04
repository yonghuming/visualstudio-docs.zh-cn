---
title: "“continue”不能位于循环外 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d2d95259-b2bc-4069-9876-60c30ad600a3
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# “continue”不能位于循环外
尝试在循环外部使用 **continue** 语句。  **continue** 语句只能用于以下循环的主体中：  
  
-   `do-while` 循环，  
  
-   `while` 循环，  
  
-   **for** 循环，  
  
-   **for\/in** 循环。  
  
### 更正此错误  
  
-   请确保 **continue** 语句出现在以下循环的主体中：  
  
    -   `do-while` 循环，  
  
    -   `while` 循环，  
  
    -   **for** 循环，  
  
    -   **for\/in** 循环。  
  
## 请参阅  
 [continue 语句](../../javascript/reference/continue-statement-javascript.md)   
 [控制程序流](../../javascript/controlling-program-flow-javascript.md)   
 [脚本疑难解答](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)