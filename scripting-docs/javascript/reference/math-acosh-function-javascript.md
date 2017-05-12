---
title: "Math.acosh 函数 (JavaScript) | Microsoft Docs"
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.acosh 函数 (JavaScript)
返回数字的双曲反余弦值（或反双曲余弦值）。  
  
## 语法  
  
```  
Math.acosh(number)  
```  
  
#### 参数  
 所需的 `number` 参数是数值表达式。  
  
## 返回值  
 `number` 参数的反双曲余弦值（以弧度表示）。  
  
## 示例  
 下面的代码演示如何使用 `acosh` 函数。  
  
```javascript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## 备注  
 **适用于**：[Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 请参阅  
 [Math.acos 函数](../../javascript/reference/math-acos-function-javascript.md)   
 [Math.asin 函数](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 函数](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 函数](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 函数](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 函数](../../javascript/reference/math-tan-function-javascript.md)   
 [Math 对象](../../javascript/reference/math-object-javascript.md)