---
title: "break 语句 (JavaScript) | Microsoft Docs"
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
  - "break_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "break 语句"
  - "do...while 语句"
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# break 语句 (JavaScript)
终止当前循环，或者，当与 `label` 一起使用时，终止相关联的语句。  
  
## 语法  
  
```  
break [label];  
```  
  
## 备注  
 可选 `label` 参数指定要中断的语句的标签。  
  
 通常在 `switch` 语句和 `while`、`for`、`for...in` 或 `do...while` 循环中使用 `break` 语句。  `label` 参数最常用于 `switch` 语句，但它可以用于任何简单或复合的语句。  
  
 执行 `break` 语句将从当前循环或语句中退出，然后使用紧随其后的语句开始执行脚本。  
  
## 示例  
 在此示例中，计数器设置为从 1 数到 99；但 `break` 语句在计数器数到 14 后终止了循环。  
  
```javascript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 在下面的代码中，`break` 语句引用 `Inner:` 语句后面的 `for` 循环。  当 `j` 等于 24 时，`break` 语句将导致程序流退出该循环。  数字 21 到 23 逐行显示。  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [continue 语句](../../javascript/reference/continue-statement-javascript.md)   
 [do...while 语句](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [for...in 语句](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [标记语句](../../javascript/reference/labeled-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)