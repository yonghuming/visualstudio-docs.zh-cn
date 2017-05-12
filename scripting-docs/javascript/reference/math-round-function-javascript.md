---
title: "Math.round 函数 (JavaScript) | Microsoft Docs"
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
  - "round"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Math 对象"
  - "Round 方法"
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.round 函数 (JavaScript)
返回所提供的舍入到最近整数的数值表达式。  
  
## 语法  
  
```  
  
Math.round(  
number  
)   
```  
  
## 备注  
 `number` 参数是必需的，表示要舍入为最接近的整数的值。  
  
 对于正数，如果 `number` 的小数部分大于或等于 0.5，则返回值为大于 `number` 的最小整数。  如果小数部分小于 0.5，则返回值为小于或等于 `number` 的最大整数。  
  
 对于负数，如果小数部分恰好为 \-0.5，则返回值为大于该数字的最小整数。  
  
 例如，`Math.round(8.5)` 返回 9，但 `Math.round(-8.5)` 返回 \-8。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## 请参阅  
 [Math.random 函数](../../javascript/reference/math-random-function-javascript.md)