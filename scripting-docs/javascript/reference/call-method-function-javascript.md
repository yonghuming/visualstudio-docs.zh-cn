---
title: "call 方法 (Function) (JavaScript) | Microsoft Docs"
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
  - "call"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "call 方法"
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# call 方法 (Function) (JavaScript)
调用一个对象的方法，用另一个对象替换当前对象。  
  
## 语法  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## 参数  
 `thisObj`  
 可选。  将作为当前对象使用的对象。  
  
 `arg1, arg2, , argN`  
 可选。  将被传递到该方法的参数列表。  
  
## 备注  
 `call` 方法用于调用代表另一项目的方法。  它允许您将函数的 `this` 对象从初始上下文变为由 `thisObj` 指定的新对象。  
  
 如果没有提供 `thisObj` 参数，则 `global` 对象被用作 `thisObj`。  
  
## 示例  
 下面的代码演示如何使用 `call` 方法。  
  
```javascript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [Function 对象](../../javascript/reference/function-object-javascript.md)   
 [apply 方法 \(Function\)](../../javascript/reference/apply-method-function-javascript.md)