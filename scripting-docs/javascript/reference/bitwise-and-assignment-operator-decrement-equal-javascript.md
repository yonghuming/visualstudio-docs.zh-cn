---
title: "按位与赋值运算符 (&amp;=) (JavaScript) | Microsoft Docs"
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
  - "&="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&= 运算符"
  - "赋值运算符，按位 [JavaScript]"
  - "AND 运算符"
  - "按位运算符，AND 运算符"
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 按位与赋值运算符 (&amp;=) (JavaScript)
对变量值与表达式值设置按位“与”运算的结果。  变量和表达式均被视为 32 位整数。  
  
## 语法  
  
```  
  
result &= expression  
```  
  
## 参数  
 `result`  
 任何变量。  
  
 `expression`  
 任何表达式。  
  
## 备注  
 使用此运算符与指定以下内容相同：  
  
```javascript  
result = result & expression  
```  
  
 [按位“与”运算符 \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)查看 `result` 和 `expression` 的二进制表示形式的值，并对它们执行按位“与”运算。  该运算的输出如下所示：  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
  
```  
  
 任何时候，只要两个表达式的某位都为 1，则结果中的该位为 1。  否则，结果中的该位为 0。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [按位“与”运算符 \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)