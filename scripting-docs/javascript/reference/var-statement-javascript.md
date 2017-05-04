---
title: "var 语句 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "var_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "声明变量，var 语句"
  - "var 语句"
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# var 语句 (JavaScript)
声明一个变量。  
  
## 语法  
  
```  
var variable1 = value1  
```  
  
## 参数  
 `variable1`  
 要声明的变量的名称。  
  
 `value1`  
 赋给变量的初始值。  
  
## 备注  
 使用 `var` 语句来声明变量。  可以在声明变量时为变量赋值，也可以稍后在脚本中给变量赋值。  
  
 一个变量在您的脚本中首次得到声明。  
  
 可以在不使用 `var` 关键字的情况下声明变量，并为该变量赋值。  这就是所谓的*隐式声明*，但不建议这样做。  隐式声明会提供一个可变的全局范围。  当您在过程级别声明变量时，通常不希望它具有全局范围。  若要避免提供可变的全局范围，则必须在变量声明中使用 `var` 关键字。  
  
 如果未在 `var` 语句中初始化您的变量，则将自动为其分配 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值 `undefined`。  
  
## 示例  
 以下示例阐释了 `var` 语句的用法。  
  
```javascript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)   
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array 对象](../../javascript/reference/array-object-javascript.md)   
 [变量](../../javascript/variables-javascript.md)