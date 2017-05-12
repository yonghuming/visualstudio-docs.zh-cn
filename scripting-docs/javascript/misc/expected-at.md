---
title: "应有“@” | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1032"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 应有“@”
尝试使用 `@set` 语句创建要用于条件编译语句的变量，但不在变量名的前面放置“**@**”符号。  
  
### 更正此错误  
  
-   立即在变量名的前面添加“**@**”符号。  例如：  
  
    ```javascript  
    @set @myvar = 1  
    ```  
  
## 请参阅  
 [@set 语句](../../javascript/reference/at-set-statement-javascript.md)   
 [条件编译](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件编译变量](../../javascript/advanced/conditional-compilation-variables-javascript.md)