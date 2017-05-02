---
title: "Math.abs 函数 (JavaScript) | Microsoft Docs"
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
  - "abs"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "绝对值，计算"
  - "绝对值"
  - "数值表达式"
  - "abs 方法"
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Math.abs 函数 (JavaScript)
返回一个数字的绝对值（即该值不考虑数字是为正还是为负）。  例如，\-5 的绝对值和 5 的绝对值相同。  
  
## 语法  
  
```  
Math.abs(number)  
```  
  
#### 参数  
 必需的 `number` 参数是绝对值所需的数值表达式。  
  
## 返回值  
 `number` 参数的绝对值。  
  
## 示例  
 下面的示例说明了 `abs` 函数的用法。  
  
```javascript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **应用于**：[Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## 请参阅  
 [Math 对象](../../javascript/reference/math-object-javascript.md)