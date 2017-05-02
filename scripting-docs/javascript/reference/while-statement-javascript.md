---
title: "while 语句 (JavaScript) | Microsoft Docs"
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
  - "while_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "循环结构，while 语句"
  - "while 语句"
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# while 语句 (JavaScript)
执行一条语句或一系列语句，直到指定条件为 `false` 为止。  
  
## 语法  
  
```  
while (expression) {  
    statements  
}   
```  
  
## 参数  
 `expression`  
 必需。  在循环的每次迭代前检查的布尔表达式。  如果 `expression` 为 `true`，则执行循环。  如果 `expression` 为 `false`，则循环会终止。  
  
 `statements`  
 可选。  如果 `expression` 为 `true`，则执行一个或多个语句。  
  
## 备注  
 `while` 语句在第一次执行循环前检查 `expression`。  如果此时 `expression` 为 `false`，则该循环永远不会执行。  
  
## 示例  
 下面的示例阐释了 `while` 语句的用法。  
  
```javascript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [continue 语句](../../javascript/reference/continue-statement-javascript.md)   
 [do...while 语句](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [for...in 语句](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)