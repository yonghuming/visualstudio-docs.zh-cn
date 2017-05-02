---
title: "toPrecision 方法 (Number) (JavaScript) | Microsoft Docs"
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
  - "toPrecision"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toPrecision 方法"
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toPrecision 方法 (Number) (JavaScript)
以指数记数法或定点记数法表示具有指定数字位数的数字。  
  
## 语法  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## 参数  
 `numObj`  
 必需。  一个 `Number` 对象。  
  
 `precision`  
 可选。  有效位数。  必须介于 1 和 21 之间（含 1 和 21）。  
  
## 返回值  
 对于以指数记数法表示的数字，将返回小数点后的 `precision` \-1 位数字。  对于以定点记数法表示的数字，将返回 `precision` 位有效位数。  
  
 如果没有提供参数 `precision` 或者它为 **undefined**，则改为调用 **toString** 方法。  
  
## 示例  
 下面的代码演示如何使用 `toPrecision`。  
  
```javascript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**：[Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## 请参阅  
 [toFixed 方法 \(Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential 方法 \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)