---
title: "按位左移运算符 (&lt;&lt;) (JavaScript) | Microsoft Docs"
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
  - "<<"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<< 运算符"
  - "<< 运算符, 关于 << 运算符"
  - "按位运算符, Left Shift 运算符"
  - "左移位运算符"
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 按位左移运算符 (&lt;&lt;) (JavaScript)
左移表达式的位。  
  
## 语法  
  
```  
  
result = expression1 << expression2  
```  
  
## 参数  
 *result*  
 任何变量。  
  
 *expression1*  
 任何表达式。  
  
 *expression2*  
 任何表达式。  
  
## 备注  
 **\<\<** 运算符将 *expression1* 的位左移 *expression2* 中指定的位数。  例如：  
  
```javascript  
var temp  
temp = 14 << 2  
```  
  
 变量 *temp* 的值为 56，因为 14（即二进制的 00001110）左移两位等于 56（即二进制的 00111000）。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [左移赋值运算符 \(\<\<\=\)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [按位右移运算符 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [无符号右移运算符 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)