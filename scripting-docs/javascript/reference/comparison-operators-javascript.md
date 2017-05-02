---
title: "比较运算符 (JavaScript) | Microsoft Docs"
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
  - "Comparison"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "比较运算符，脚本"
  - "大于运算符"
  - "比较运算符"
  - "大于或等于运算符"
  - "不等运算符"
  - "恒等运算符"
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 比较运算符 (JavaScript)
返回指示比较结果的布尔值。  
  
## 语法  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## 参数  
 `expression1`  
 任何表达式。  
  
 `comparisonoperator`  
 任何比较运算符。  
  
 `expression2`  
 任何表达式。  
  
## 备注  
 比较字符串时，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 使用字符串表达式的 Unicode 字符值。  
  
 下面描述根据 `expression1` 和 `expression2` 的类型和值，不同组的运算符是如何起作用的：  
  
 关系运算符：`<`、`>`、`<=`、`>=`  
  
-   尝试将 `expression1` 和 `expression2` 转换为数字。  
  
-   如果两个表达式均为字符串，则进行字符串比较。  
  
-   如果任一表达式为 `NaN`，则返回 `false`。  
  
-   负零等于正零。  
  
-   负无穷小于包括其自身在内的任何数。  
  
-   正无穷大于包括其自身在内的任何数。  
  
 相等运算符：`==`、`!=`  
  
-   如果两个表达式的类型不同，则尝试将它们转换为字符串、数字或布尔值。  
  
-   `NaN` 与包括其自身在内的任何值都不相等。  
  
-   负零等于正零。  
  
-   `null` 与 `null` 和 `undefined` 相等。  
  
-   以下情况被认为是相等的：相同的字符串，数值上相等的数字，同一对象，相同的布尔值，或者当类型不同时可以被强制转换为上述情况之一的值。  
  
-   其他比较都被认为是不等的。  
  
 恒等运算符：`===`、`!==`  
  
 这些运算符的行为与相等运算符的行为相同，只不过不会执行类型转换。  如果两个表达式的类型不相同，则这些表达式始终返回 `false`。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)