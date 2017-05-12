---
title: "右移赋值运算符 (&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>= 运算符 [JavaScript]"
  - "赋值运算符, JavaScript"
  - "右移位运算符 [JavaScript]"
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 右移赋值运算符 (&gt;&gt;=) (JavaScript)
变量值右移表达式值指定的位数，保持符号不变，并将结果赋给该变量。  
  
## 语法  
  
```  
  
result >>= expression  
```  
  
## 参数  
 *result*  
 任何变量。  
  
 *expression*  
 任何表达式。  
  
## 备注  
 使用 **\>\>\=** 运算符与指定以下内容完全相同：  
  
```javascript  
result = result >> expression  
```  
  
 **\>\>\=** 运算符将*结果* 的所有位右移*表达式* 指定的位数。  用 *result* 的符号位填充右移后左边空出的位。  右移的位被丢弃。  例如，计算完下列代码后，*temp* 的值为 \-4：因为 14（即二进制的 11110010）右移两位后等于 \-4（即二进制的 11111100）。  
  
```javascript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [按位左移运算符 \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [按位右移运算符 \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [无符号右移运算符 \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)