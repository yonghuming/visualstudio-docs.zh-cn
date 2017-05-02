---
title: "if...else 语句 (JavaScript) | Microsoft Docs"
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
  - "else_JavaScriptKeyword"
  - "if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "if 语句, if...else"
  - "循环结构, if...else 语句"
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# if...else 语句 (JavaScript)
根据表达式的值有条件地执行一组语句。  
  
## 语法  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## 参数  
 `condition1`  
 必需。  布尔表达式。  如果 `condition1` 为 `null` 或 `undefined`，则 `condition1` 将被视为 `false`。  
  
 `statement1`  
 可选。  `condition1` 为 **true** 时要执行的语句。  可以是复合语句。  
  
 `condition2`  
 要计算的条件。  
  
 `statement2`  
 可选。  `condition2` 为 `true` 时要执行的语句。  可以是复合语句。  
  
 `statement3`  
 如果 `condition1` 和 `condition2` 都为 `false`，则执行此语句。  
  
## 示例  
 下面的代码演示如何使用 `if`、`if else` 和 `else`。  
  
 将 `statement1` 和 `statement2` 包含在大括号 \({}\) 内通常是一个好的作法，这样就很清楚，并可以避免无意中造成的错误。  
  
```javascript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [条件（三元）运算符 \(?:\)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)