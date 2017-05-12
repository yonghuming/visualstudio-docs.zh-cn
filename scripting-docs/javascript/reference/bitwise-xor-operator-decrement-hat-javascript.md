---
title: "按位异或运算符 (^) (JavaScript) | Microsoft Docs"
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
  - "^"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "按位运算符, XOR 运算符"
  - "XOR 运算符"
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 按位异或运算符 (^) (JavaScript)
对两个表达式执行按位“异或”运算。  
  
## 语法  
  
```  
  
result = expression1 ^ expression2  
```  
  
## 参数  
 *result*  
 任何变量。  
  
 *expression1*  
 任何表达式。  
  
 *expression2*  
 任何表达式。  
  
## 备注  
 **^** 运算符随后查看两个表达式的二进制表示形式的值，并执行按位“异或”运算。  此运算的结果如下所示：  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 当且仅当只有一个表达式的某位为 1 时，结果中的该位才为 1。  否则，结果中的该位为 0。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [按位“异或”赋值运算符 \(^\=\)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)