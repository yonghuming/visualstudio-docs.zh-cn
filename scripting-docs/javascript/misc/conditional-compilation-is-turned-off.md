---
title: "条件编译已关闭 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 条件编译已关闭
尝试在未先启用条件编译的情况下使用条件编译变量。  启用条件编译将告知 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 编译器将以 @ 开头的标识符解释为条件编译变量。  可以使用以下语句开始条件代码以完成此操作：  
  
```  
/*@cc_on @*/  
```  
  
### 更正此错误  
  
-   将以下语句添加到条件代码的开头：  
  
    ```javascript  
    /*@cc_on @*/  
    ```  
  
## 请参阅  
 [条件编译](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件编译变量](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on 语句](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if 语句](../../javascript/reference/at-if-statement-javascript.md)   
 [@set 语句](../../javascript/reference/at-set-statement-javascript.md)