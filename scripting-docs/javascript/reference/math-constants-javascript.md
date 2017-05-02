---
title: "Math 常量 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "LN2 常量 [JavaScript]"
  - "E 常量 [JavaScript]"
  - "LOG10E 常量 [JavaScript]"
  - "SQRT1_2 常量 [JavaScript]"
  - "LOG2E 常量 [JavaScript]"
  - "Math.SQRT2 常量 [JavaScript]"
  - "PI 常量 [JavaScript]"
  - "Math.LOG2E 常量 [JavaScript]"
  - "常量 [JavaScript]，数学"
  - "Math.E 常量 [JavaScript]"
  - "对数常量 [JavaScript]"
  - "Math.LOG10E 常量 [JavaScript]"
  - "Math.SQRT1_2 常量 [JavaScript]"
  - "SQRT2 常量 [JavaScript]"
  - "平方根常量 [JavaScript]"
  - "Math.PI 常量 [JavaScript]"
  - "算术常量 [JavaScript]"
  - "LN10 常量 [JavaScript]"
  - "Math.LN2 常量 [JavaScript]"
  - "Math.LN10 常量 [JavaScript]"
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math 常量 (JavaScript)
Math 常量返回的常量值是 `Math` 对象的属性。  
  
## Math 对象常量  
 下表列出的常量值是 [Math 对象](../../javascript/reference/math-object-javascript.md)的属性。  
  
|常量|描述|约值|  
|--------|--------|--------|  
|`Math.E`|数学常量 e。  这是欧拉数，即自然对数的底。|2.718|  
|`Math.LN2`|2 的自然对数。|0.693|  
|`Math.LN10`|10 的自然对数。|2.302|  
|`Math.LOG2E`|e 的以 2 为底的对数。|1.443|  
|`Math.LOG10E`|e 的以 10 为底的对数。|0.434|  
|`Math.PI`|Pi.  这是圆的周长与直径的比率。|3.14159|  
|`Math.SQRT1_2`|0.5 的平方根或相等项（即 2 的平方根分之一）。|0.707|  
|`Math.SQRT2`|2 的平方根。|1.414|  
  
## 示例  
 以下示例阐释了 `Math.PI` 常量的用法。  
  
```javascript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **应用于**：[Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## 请参阅  
 [Number 常量](../../javascript/reference/number-constants-javascript.md)   
 [JavaScript 常量](../../javascript/reference/javascript-constants.md)