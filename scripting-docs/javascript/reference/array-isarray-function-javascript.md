---
title: "Array.isArray 函数 (JavaScript) | Microsoft Docs"
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
  - "Array.isArray 函数 [JavaScript]"
  - "isArray 函数 [JavaScript]"
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Array.isArray 函数 (JavaScript)
确定对象是否为数组。  
  
## 语法  
  
```  
Array.isArray(object)   
```  
  
#### 参数  
 `object`  
 必需。  要测试的对象。  
  
## 返回值  
 如果 `object` 是数组，则为 `true`；否则为 `false`。  如果 `object` 参数不是对象，则返回 `false`。  
  
## 示例  
 下面的示例阐释了 `Array.isArray` 函数的用法。  
  
```javascript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## 要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 请参阅  
 [Array 对象](../../javascript/reference/array-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)   
 [typeof 运算符](../../javascript/reference/typeof-operator-decrementjavascript.md)