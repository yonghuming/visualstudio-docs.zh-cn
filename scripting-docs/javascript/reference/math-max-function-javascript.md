---
title: "Math.max 函数 (JavaScript) | Microsoft Docs"
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
  - "max"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "max 方法"
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.max 函数 (JavaScript)
返回所提供的一组数值表达式中的较大者。  
  
## 语法  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## 备注  
 可选 `number1, number2, ..., numberN` 参数是要计算的数值表达式。  
  
 如果未提供参数，则返回值等于 [Number.NEGATIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md)。  如果任何参数为 `NaN`，则返回值也为 `NaN`。  
  
## 示例  
 下面的代码演示如何获取两个表达式中的较大者。  
  
```javascript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [Math.min 函数](../../javascript/reference/math-min-function-javascript.md)