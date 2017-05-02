---
title: "按位取反运算符 (~) (JavaScript) | Microsoft Docs"
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
  - "~"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "按位运算符, NOT 运算符"
  - "NOT 运算符"
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 按位取反运算符 (~) (JavaScript)
对一个表达式执行位非（求非）运算。  
  
## 语法  
  
```  
  
result = ~ expression  
```  
  
## 参数  
 *result*  
 任何变量。  
  
 *expression*  
 任何表达式。  
  
## 备注  
 所有一元运算符（如 `~` 运算符）都按照下面的规则来计算表达式的值：  
  
-   如果应用于未定义的表达式或 `null` 表达式，则会引发一个运行时错误。  
  
-   将对象转换为字符串。  
  
-   如果可能，将字符串转换为数字。  否则，将引发运行时错误。  
  
-   布尔值被视为数字（如果为 false，则为 0；如果为 true，则为 1）。  
  
 运算符将应用于结果数字。  
  
 `~` 运算符查看表达式的二进制表示形式的值，并执行位非运算。  
  
 表达式中的任何一位为 1，则结果中的该位变为 0。  表达式中的任何一位为 0，则结果中的该位变为 1。  
  
 下面的示例阐释了位非 \(~\) 运算符的用法。  
  
```  
var temp = ~5;  
```  
  
 所得值为 \-6，如下表所示。  
  
|表达式|二进制值（2 的补数）|十进制值|  
|---------|-----------------|----------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|\-6|  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [逻辑“非”运算符 \(\!\)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)