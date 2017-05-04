---
title: "for 语句 (JavaScript) | Microsoft Docs"
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
  - "for_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "循环结构, for 语句"
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# for 语句 (JavaScript)
只要满足指定的条件，就执行一个语句块。  
  
## 语法  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## 参数  
 `initialization`  
 可选。  一个表达式。  该表达式在执行循环前仅被执行一次。  
  
 `test`  
 可选。  布尔表达式。  如果 `test` 为 `true`，则执行 `statement`。  如果 `test` 为 `false`，则终止循环。  
  
 `increment`  
 可选。  一个表达式。  在每次通过循环的结尾时执行该增量表达式。  
  
 `statement`  
 可选。  如果 `test` 为 **true**，则执行一个或多个语句。  可以是复合语句。  
  
## 备注  
 在需要将循环执行已知次数时，通常使用 `for` 循环。  `for` 循环对于迭代数组以及执行顺序处理很有用。  
  
 条件表达式的测试发生在循环执行之前，因此 `for` 语句执行零次或多次。  
  
 在 `for` 循环语句块中的任何行上，都可以使用 `break` 语句来退出循环，或者可以使用 `continue` 语句将控制权移交给循环的下一迭代。  
  
## 示例  
 在下面的示例中，`for` 语句执行括起来的语句，如下所示：  
  
-   首先，计算变量 `i` 的初始值。  
  
-   然后，只要 `i` 的值小于或等于 9，就会执行 `document.write` 语句并重新计算 `i`。  
  
-   当 `i` 大于 9 时，条件变为 false 并且将控制权移交到循环外部。  
  
```javascript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## 示例  
 `for` 语句的所有表达式都是可选的。  在下面的示例中，`for` 语句创建一个无限循环，`break` 语句用于退出循环。  
  
```javascript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [for...in 语句](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)