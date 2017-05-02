---
title: "按位与运算符 (&amp;) (JavaScript) | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "赋值运算符，按位 [JavaScript]"
  - "& 运算符，关于 & 运算符"
  - "AND 运算符"
  - "& 运算符"
  - "按位运算符，AND 运算符"
  - "& 运算符，按位运算符"
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 按位与运算符 (&amp;) (JavaScript)
对两个 32 位表达式执行按位“与”运算。  
  
## 语法  
  
```  
  
result = expression1 & expression2  
```  
  
## 参数  
 `result`  
 运算的结果。  
  
 `expression1`  
 任何表达式。  
  
 `expression2`  
 任何表达式。  
  
## 备注  
 `&` 对两个 32 位表达式的每一个位执行按位“与”运算。  如果两个位均为 1，则结果是 1。  否则，结果为 0。  
  
|Bit1|Bit2|ANDed 值|  
|----------|----------|-------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 下面的示例演示如何使用 `&` 运算符。  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [按位“与”赋值运算符 \(&\=\)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)