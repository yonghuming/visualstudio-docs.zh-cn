---
title: "无符号右移位赋值运算符 (&gt;&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>>= 运算符"
  - "赋值运算符, JavaScript"
  - "无符号右移位赋值运算符 (>>>=)"
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 无符号右移位赋值运算符 (&gt;&gt;&gt;=) (JavaScript)
变量值右移表达式值指定的位数，但不保持符号，并将结果赋给该变量。  
  
## 语法  
  
```  
  
result >>>= expression  
```  
  
## 参数  
 *result*  
 任何变量。  
  
 *expression*  
 任何表达式。  
  
## 备注  
 使用 \>\>\>\= 运算符与执行以下操作完全相同：  
  
```javascript  
result = result >>> expression  
```  
  
 **\>\>\>\=** 运算符将 *result* 的各位向右移在 *expression* 中指定的位数。  用零填充右移后左边空出的位。  右移的位被丢弃。  例如：  
  
```javascript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 变量 *temp* 的初始值为 \-14（二进制补码为 11111111 11111111 11111111 11110010）。  向右移两位后，该值等于 1073741820（二进制为 00111111 11111111 11111111 11111100）。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [无符号右移运算符 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [按位左移运算符 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [按位右移运算符 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)