---
title: "parseFloat 函数 (JavaScript) | Microsoft Docs"
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
  - "parseFloat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseFloat 方法"
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# parseFloat 函数 (JavaScript)
将字符串转换为浮点数。  
  
## 语法  
  
```  
parseFloat(numString)   
```  
  
## 备注  
 必需的 `numString` 参数是一个包含浮点数的字符串。  
  
 `parseFloat` 函数返回一个等于 `numString` 中包含的数字的数值。  如果没有 `numString` 的前缀可以被成功地分析为浮点数，则返回 `NaN`（非数字）。  
  
```javascript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 可使用 `isNaN` 函数测试是否为 `NaN`。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Global 对象](../../javascript/reference/global-object-javascript.md)  
  
## 请参阅  
 [isNaN 函数](../../javascript/reference/isnan-function-javascript.md)   
 [parseInt 函数](../../javascript/reference/parseint-function-javascript.md)   
 [String 对象](../../javascript/reference/string-object-javascript.md)