---
title: "continue 语句 (JavaScript) | Microsoft Docs"
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
  - "continue_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue 语句"
  - "do...while 语句"
  - "循环结构, continue 语句"
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# continue 语句 (JavaScript)
停止循环的当前迭代，并开始新的迭代。  
  
## 语法  
  
```  
continue [label];  
```  
  
## 备注  
 可选的 `label` 参数指定 `continue` 所适用于的语句。  
  
 只能在 `while`、`do...while`、**for** 或 `for...in` 循环内使用 `continue` 语句。  执行 `continue` 语句将停止循环的当前迭代，并从循环的开始处继续程序流。  这对于不同类型的循环有以下各种影响：  
  
-   `while` 和 `do...while` 循环测试其条件，如果符合条件，则再次执行循环。  
  
-   `for` 循环执行其递增表达式，如果测试表达式为真，则再次执行循环。  
  
-   `for...in` 循环前往指定变量的下一个字段，并再次执行循环。  
  
## 示例  
 在此示例中，循环从 1 迭代到 9。  由于将 `continue` 语句与表达式 `(i < 5)` 一起使用，因此跳过 `continue` 与 `for` 循环体末尾之间的语句。  
  
```javascript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 在以下代码中，`continue` 语句引用前方有 `Inner:` 标签的 `for` 循环。  当 `j` 为 24 时，`continue` 语句使 `for` 循环进入下一个迭代。  数字 21 到 23 以及 25 到 30 逐行显示。  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [do...while 语句](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [for...in 语句](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [标记语句](../../javascript/reference/labeled-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)