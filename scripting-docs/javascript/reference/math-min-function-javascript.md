---
title: "Math.min 函数 (JavaScript) | Microsoft Docs"
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
  - "min"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "min 方法"
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.min 函数 (JavaScript)
返回一组数值表达式中的较小者。  
  
## 语法  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## 备注  
 可选 `number1, number2, ..., numberN` 参数是要计算的数值表达式。  
  
 如果未提供参数，则返回值等于 [Number.POSITIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md)。  如果任何参数为 `NaN`，则返回值也为 `NaN`。  
  
## 示例  
 下面的代码演示如何获取两个表达式中的较小者。  
  
```javascript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [Math.max 函数](../../javascript/reference/math-max-function-javascript.md)