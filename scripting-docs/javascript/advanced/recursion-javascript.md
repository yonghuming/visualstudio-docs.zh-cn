---
title: "递归 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "函数，递归函数调用"
  - "递归过程"
  - "函数调用，递归"
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 递归 (JavaScript)
递归是一项非常重要的编程技巧，函数通过它调用其本身。  
  
## 递归示例  
 示例之一就是阶乘的计算。  数字 *n* 的阶乘通过乘以 1 \* 2 \* 3 \*...  *n* 进行计算。  下面的示例演示如何使用计算结果的 `while` 循环反复计算阶乘。  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    var tmp = num;  
    while (num-- > 2) {  
        tmp *= num;  
    }  
    return tmp;  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```  
  
 可以使示例递归变得非常简单。  只需再次调用 `factorial` 并传入下一个最小值，而不是使用 `while` 循环计算此值。  当此值为 1 时，递归将停止。  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    // Otherwise, call this recursive procedure again.  
    else {  
        return (num * factorial(num - 1));  
    }  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```