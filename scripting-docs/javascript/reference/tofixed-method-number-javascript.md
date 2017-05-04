---
title: "toFixed 方法 (Number) (JavaScript) | Microsoft Docs"
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
  - "toFixed"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toFixed 方法"
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# toFixed 方法 (Number) (JavaScript)
使用定点表示法表示数字。  
  
## 语法  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## 参数  
 `numObj`  
 需要一个 `Number` 对象。  
  
 `fractionDigits`  
 可选。  小数点后的位数。  值必须介于 0 \-20 之间（含 1 和 21）。  
  
## 返回值  
 返回一个字符串，表示一个以定点表示法表示的数字，其中小数点后包含 `fractionDigits` 位。  
  
 如果没有提供 `fractionDigits` 参数或该参数是**未定义**的，则默认值为 0。  
  
## 示例  
 下面的代码演示如何使用 `toFixed`。  
  
```javascript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **应用于**：[Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## 请参阅  
 [toExponential 方法 \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision 方法 \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)