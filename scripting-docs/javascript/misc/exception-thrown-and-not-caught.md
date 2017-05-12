---
title: "引发了但未捕获异常 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5022"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 引发了但未捕获异常
您在代码中包括一个 `throw` 语句，但该语句未包含在 **try** 块中，或者没有关联的 **catch** 块会捕获错误。  使用 **throw** 语句在 **try** 块的内部引发异常，并使用 **catch** 语句在 **try** 块的外部捕获异常。  
  
### 更正此错误  
  
-   包含可在 **try** 块中引发异常的代码，并确保存在相应的 **catch** 块。  
  
-   确保您的 catch 语句应为正确的异常格式。  
  
-   如果重新引发异常，请确保存在另一个相应的 catch 语句。  
  
## 请参阅  
 [Error 对象](../../javascript/reference/error-object-javascript.md)   
 [throw 语句](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 语句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)