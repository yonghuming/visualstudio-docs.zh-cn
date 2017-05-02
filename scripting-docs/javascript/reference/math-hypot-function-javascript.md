---
title: "Math.hypot 函数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Math.hypot 函数 (JavaScript)
返回参数平方和的平方根。  
  
## 语法  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### 参数  
 `value1`  
 必需。  第一个数字。  
  
 `value2`  
 可选。  第二个数字。  
  
 `values`  
 可选。  一个或多个数字。  
  
## 备注  
 如果有任意参数为 NaN，则该函数返回 NaN。  如果未提供任何参数，则该函数返回 0。  
  
## 示例  
 下面的示例演示一个使用 `Math.hypot` 函数的示例。  
  
```javascript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]