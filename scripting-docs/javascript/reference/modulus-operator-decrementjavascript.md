---
title: "取模运算符 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "%"
dev_langs: 
  - "JavaScript"
  - "DHTML"
helpviewer_keywords: 
  - "取模运算符，JavaScript"
  - "运算符百分比 [JavaScript]"
  - "取模函数 [JavaScript]"
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 取模运算符 (JavaScript)
一个表达式的值除以另一个表达式的值，并返回余数。  
  
## 语法  
  
```  
  
result = number1 % number2  
```  
  
## 参数  
 `result`  
 任何变量。  
  
 `number1`  
 任何数值表达式。  
  
 `number2`  
 任何数值表达式。  
  
## 备注  
 取模或余数运算符用 `number2` 除 `number1` 并只将余数返回为 `result`。  `result` 中的符号与 `number1` 的符号相同。  `result` 的值在 0 和 `number2` 的绝对值之间。  
  
 下面的代码演示如何使用取模运算符。  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)