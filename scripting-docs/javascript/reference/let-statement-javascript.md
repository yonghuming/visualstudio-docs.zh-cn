---
title: "let 语句 (JavaScript) | Microsoft Docs"
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
  - "let_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "let 语句"
  - "声明变量，let 语句"
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# let 语句 (JavaScript)
声明一个块范围变量。  
  
## 语法  
  
```  
let variable1 = value1  
```  
  
#### 参数  
 `variable1`  
 要声明的变量的名称。  
  
 `value1`  
 赋给变量的初始值。  
  
## 备注  
 使用 `let` 语句声明一个变量，该变量的范围限于声明它的块中。  可以在声明变量时为变量赋值，也可以稍后在脚本中给变量赋值。  
  
 使用 `let` 声明的变量，在声明前无法使用，否则将会导致错误。  
  
 如果未在 `let` 语句中初始化您的变量，则将自动为其分配 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值 `undefined`。  
  
## 示例  
 下面的示例阐释了 `let` 语句的用法。  
  
```javascript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [const 语句](../../javascript/reference/const-statement-javascript.md)   
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array 对象](../../javascript/reference/array-object-javascript.md)   
 [变量](../../javascript/variables-javascript.md)