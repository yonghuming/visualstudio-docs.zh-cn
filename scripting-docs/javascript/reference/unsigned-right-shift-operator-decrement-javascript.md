---
title: "无符号右移位运算符 (&gt;&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>> 运算符"
  - "无符号右移位运算符 (>>>)"
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 无符号右移位运算符 (&gt;&gt;&gt;) (JavaScript)
右移表达式的位，不保留符号。  
  
## 语法  
  
```  
  
result = expression1 >>> expression2  
```  
  
## 参数  
 *result*  
 任何变量。  
  
 *expression1*  
 任何表达式。  
  
 *expression2*  
 任何表达式。  
  
## 备注  
 **\>\>\>** 运算符将 *expression1* 的位右移 *expression2* 中指定的位数。  用零填充右移后左边空出的位。  右移的位被丢弃。  例如：  
  
```javascript  
var temp  
temp = -14 >>> 2  
```  
  
 变量 *temp* 具有初始值 \-14（二进制补码 11111111 11111111 11111111 11110010）。  其右移两位后，值等于 1073741820（即二进制的 00111111 11111111 11111111 11111100）。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [无符号右移赋值运算符 \(\>\>\>\=\)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [按位左移运算符 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [按位右移运算符 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)