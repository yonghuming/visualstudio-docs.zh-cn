---
title: "按位右移运算符 (&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">> 运算符"
  - ">> 运算符, 关于 >> 运算符"
  - ">> 运算符, 位组"
  - "按位运算符, 右移位运算符"
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 按位右移运算符 (&gt;&gt;) (JavaScript)
右移表达式的位，保持符号不变。  
  
## 语法  
  
```  
  
result = expression1 >> expression2  
```  
  
## 参数  
 *result*  
 任何变量。  
  
 *expression1*  
 任何表达式。  
  
 *expression2*  
 任何表达式。  
  
## 备注  
 \>\> 运算符将 *expression1* 的位右移 *expression2* 中指定的位数。  用 *expression1* 的符号位填充右移后左边空出来的位。  右移的位被丢弃。  例如，计算完下列代码后，*temp* 的值为 \-4：因为 \-14（即二进制的 11110010）右移两位后等于 \-4（即二进制的 11111100）。  
  
```javascript  
var temp  
temp = -14 >> 2  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [按位左移运算符 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [右移赋值运算符 \(\>\>\=\)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [无符号右移运算符 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)