---
title: "toExponential 方法 (Number) (JavaScript) | Microsoft Docs"
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
  - "toExponential"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toExponential 方法"
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toExponential 方法 (Number) (JavaScript)
使用指数记数法表示数字。  
  
## 语法  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## 参数  
 `numObj`  
 必需。  **Number** 对象。  
  
 `fractionDigits`  
 可选。  小数点后数字的位数。  值必须介于 0 \-20 之间（含 0 和 20）。  
  
## 返回值  
 返回用指数记数法表示的数字的字符串表示形式。  该字符串中小数点之前包含一位数字，而小数点之后可以包含 `fractionDigits` 位数字。  
  
 如果没有提供 `fractionDigits`，则 `toExponential` 方法将返回足够多位数字，以便唯一指定该数字。  
  
## 示例  
  
```javascript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## 请参阅  
 [toFixed 方法 \(Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision 方法 \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)