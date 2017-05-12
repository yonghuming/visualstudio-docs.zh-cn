---
title: "const 语句 (JavaScript) | Microsoft Docs"
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
  - "const_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "声明变量，const 语句"
  - "const 语句"
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# const 语句 (JavaScript)
通过一个常数值声明一个块范围变量。  
  
## 语法  
  
```  
const constant1 = value1  
```  
  
#### 参数  
 `constant1`  
 要声明的变量的名称。  
  
 `value1`  
 赋给变量的初始值。  
  
## 备注  
 使用 `const` 语句声明一个带常数值的变量，该变量的范围限于声明它的块中。  无法更改变量值。  
  
 使用 `const` 声明变量时必须对其进行初始化。  
  
## 示例  
 下面的示例阐释了 `const` 语句的用法。  
  
```javascript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 请参阅  
 [let 语句](../../javascript/reference/let-statement-javascript.md)   
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array 对象](../../javascript/reference/array-object-javascript.md)   
 [变量](../../javascript/variables-javascript.md)