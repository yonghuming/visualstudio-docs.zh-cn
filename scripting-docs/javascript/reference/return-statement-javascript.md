---
title: "return 语句 (JavaScript) | Microsoft Docs"
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
  - "return_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "function 语句"
  - "return 语句"
  - "return 语句, 脚本中的退出函数"
  - "return 语句, 语法"
  - "终止执行"
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# return 语句 (JavaScript)
从当前函数退出，并从该函数返回一个值。  
  
## 语法  
  
```  
  
return[(][expression][)];   
```  
  
## 备注  
 可选*表达式*参数是从该函数返回的值。  如果省略，则该函数不返回值。  
  
 使用 `return` 语句来终止一个函数的执行，并返回 *expression* 的值。  如果*表达式*被省略，或在函数内没有执行 `return` 语句，则把未定义值赋给调用当前函数的表达式。  
  
## 示例  
 下面的示例阐释了 `return` 语句的用法。  
  
```javascript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## 示例  
 下面的示例阐释了 `return` 语句在返回函数的用法。  
  
```javascript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)