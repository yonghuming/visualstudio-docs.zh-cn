---
title: "Array.of 函数（数组）(JavaScript) | Microsoft Docs"
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Array.of 函数（数组）(JavaScript)
从传入的参数返回一个数组。  
  
## 语法  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### 参数  
 `element0,...,elementN`  
 可选。  要置于数组中的元素。  这将创建一个具有 n \+ 1 个元素且长度为 n \+ 1 的数组。  
  
## 备注  
 此函数类似于调用 `new Array(args)`，但当传入一个参数时，`Array.of` 不包括特殊行为。  
  
## 示例  
 下面的示例基于传入的数字创建一个数组。  
  
```javascript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1  
  
```  
  
## 示例  
 下面的示例演示使用 `Array.of` 与 `new Array` 之间的差异。  
  
```javascript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]