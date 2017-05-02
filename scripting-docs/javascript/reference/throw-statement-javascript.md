---
title: "throw 语句 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "throw_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "错误处理，throw 语句"
  - "throw 语句"
ms.assetid: 75cbade0-fb81-4ffe-b187-b71be380bb05
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# throw 语句 (JavaScript)
生成一个可由 `try...catch...finally` 语句处理的错误条件。  
  
## 语法  
  
```  
throw exception   
```  
  
## 备注  
 必需的 `exception` 参数可以是任何表达式。  
  
 以下示例在 `try` 块中引发错误，并在 `catch` 中对其进行捕获。  
  
```javascript  
try {  
        throw new Error(200, "x equals zero");  
}  
catch (e) {  
    document.write(e.message);  
}  
  
// Output: x equals zero.  
  
```  
  
## 要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 请参阅  
 [try...catch...finally 语句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error 对象](../../javascript/reference/error-object-javascript.md)