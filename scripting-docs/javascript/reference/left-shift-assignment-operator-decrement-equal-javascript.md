---
title: "左移赋值运算符 (&lt;&lt;=) (JavaScript) | Microsoft Docs"
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
  - "<<="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<<= 运算符 [JavaScript]"
  - "左移赋值运算符 (<<=) [JavaScript]"
  - "左移位运算符 [JavaScript]"
  - "赋值运算符，JavaScript"
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 左移赋值运算符 (&lt;&lt;=) (JavaScript)
向左移动指定的位数，然后将结果赋给 `result`。  此操作空出的数位将用 0 填充。  
  
## 语法  
  
```  
  
result <<= expression  
```  
  
## 参数  
 `result`  
 任何变量。  
  
 `expression`  
 要移动的位数。  
  
## 备注  
 使用 `<<=` 运算符与指定 `result = result << expression` 完全相同  
  
 下面的示例演示如何使用 `<<=` 运算符。  
  
```javascript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [按位左移运算符 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [按位右移运算符 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [无符号右移运算符 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)