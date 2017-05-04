---
title: "应有“catch” | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1033"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 应有“catch”
您使用了异常处理 **try** 块，但未编写关联的 **catch** 语句。  异常处理机制需要将可失败的代码以及发生异常时不应执行的代码包装在 **try** 块中。  使用 **throw** 语句在 **try** 块的内部引发异常，并使用一个或多个 **catch** 语句在 **try** 块的外部捕获异常。  
  
### 更正此错误  
  
-   添加关联的 **catch** 块。  
  
-   尝试使用 **finally** 块，而不是使用 **catch** 块。  
  
## 请参阅  
 [try...catch...finally 语句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error 对象](../../javascript/reference/error-object-javascript.md)