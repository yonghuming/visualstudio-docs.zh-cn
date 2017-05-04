---
title: "Math.log 函数 (JavaScript) | Microsoft Docs"
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
  - "log"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "log 方法"
  - "Math 对象"
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Math.log 函数 (JavaScript)
返回某个数字的自然对数（底为 `e`）。  
  
## 语法  
  
```  
Math.log(number)   
```  
  
#### 参数  
 数值  
 数字。  
  
## 返回值  
 如果 `number` 为正，则此函数返回该数字的自然对数。  如果 `number` 为负，则函数返回 `NaN`。  如果 `number` 为 0，则此功能返回 `-Infinity`。  
  
## 示例  
 以下代码演示如何使用此函数。  
  
```javascript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **应用于**：[Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## 请参阅  
 [Math.sqrt 函数](../../javascript/reference/math-sqrt-function-javascript.md)