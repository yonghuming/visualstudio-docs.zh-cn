---
title: "Math.imul 函数 (JavaScript) | Microsoft Docs"
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.imul 函数 (JavaScript)
返回被视为 32 位带符号整数的两个数字的积。  
  
## 语法  
  
```  
Math.imul(x, y);  
```  
  
#### 参数  
 `x`  
 必需。  第一个数字。  
  
 `y`  
 必需。  第二个数字。  
  
## 备注  
 此函数用于编译器（如 Emscripten 和 Mandreel），它实现整数乘法的方式与 JavaScript 不同。  
  
## 示例  
 下面的代码示例演示如何使用 `Math.imul` 进行数字相乘。  
  
```javascript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]