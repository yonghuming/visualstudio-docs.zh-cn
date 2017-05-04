---
title: "do...while 语句 (JavaScript) | Microsoft Docs"
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
  - "do_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "do...while 语句"
  - "终止循环"
  - "循环结构，do 和 do-while"
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# do...while 语句 (JavaScript)
将一个语句块执行一次，然后重复该循环的执行，直到条件表达式为 `false`。  
  
## 语法  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## 参数  
 `statement`  
 必需。  `expression` 为 `true` 时要执行的语句。  可以是复合语句。  
  
 `expression`  
 必需。  一个可以被强迫转换为布尔值 `true` 或 `false` 的表达式。  如果 `expression` 为 `true`，则再次执行循环。  如果 `expression` 为 `false`，则循环会终止。  
  
## 备注  
 与 `while` 语句不同的是，`do...while` 循环会在计算条件表达式之前执行一次。  
  
 在 `do…while` 块中的任何行上，都可以使用 `break` 语句来导致程序流退出循环，或者可以使用 `continue` 语句直接转到 `while` 表达式。  
  
## 示例  
 在下面的示例中，只要变量 `i` 小于 10，`do...while` 循环中的语句就会继续执行。  
  
```javascript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## 示例  
 在以下示例中，即使未满足条件，循环内的语句也只执行一次。  
  
```javascript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## 要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [continue 语句](../../javascript/reference/continue-statement-javascript.md)   
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [for...in 语句](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)   
 [标记语句](../../javascript/reference/labeled-statement-javascript.md)