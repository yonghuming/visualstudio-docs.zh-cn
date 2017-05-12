---
title: "Math.acos 函数 (JavaScript) | Microsoft Docs"
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
  - "acos"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "acos 方法"
  - "反余弦方法"
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.acos 函数 (JavaScript)
返回一个数字的反余弦（或逆余弦）。  
  
## 语法  
  
```  
Math.acos(number)  
```  
  
#### 参数  
 必需的 `number` 参数是数值表达式。  
  
## 返回值  
 `number` 参数的反余弦值，以弧度为单位。  
  
## 示例  
 以下代码演示如何使用 `acos` 函数。  
  
```javascript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## 备注  
 **应用于**：[Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [Math.asin 函数](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 函数](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 函数](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 函数](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 函数](../../javascript/reference/math-tan-function-javascript.md)   
 [Math 对象](../../javascript/reference/math-object-javascript.md)